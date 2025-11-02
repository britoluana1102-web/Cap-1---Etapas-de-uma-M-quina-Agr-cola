# Cap-1---Etapas-de-uma-M-quina-Agricola
> # 🌾 Fase 3 - Banco de Dados Oracle - Sistema de Irrigação Inteligente
> 
> **Disciplina:** Cognitive Data Science  
> **Curso:** Inteligência Artificial - FIAP  
> **Aluna:** Luana Brito da Silva  
> **RM:** 566632  
> 
> ---
> 
> ## 📋 Sobre o Projeto
> Este projeto faz parte da **Fase 3 do PBL** da FarmTech Solutions, focado em soluções de **Agricultura 4.0**.  
> O objetivo é armazenar os dados do **Sistema de Irrigação Inteligente com ESP32** em um banco de dados **Oracle** e realizar consultas SQL para análise dos dados.
> 
> ---
> 
> ## 🔧 Tecnologias Utilizadas
> - Oracle SQL Developer & Database  
> - CSV para importação  
> - SQL  
> - GitHub  
> 
> ---
> 
> ## 📁 Estrutura do Repositório
> ```
> fase3/
> ├── dados/dados_sensores_farmtech.csv
> ├── prints/               # Prints das etapas importantes
> ├── README.md
> └── video_demonstracao.txt
> ```
> 
> ---
> 
> ## 🚀 Passo a Passo com Imagens e Consultas
> 
> ### 1️⃣ Importação do CSV
> Importação da tabela `DADOS_IRRIGACAO_RM566632` com **30 registros**.  
> <img width="1423" height="1009" alt="Captura de tela 2025-11-01 215402" src="https://github.com/user-attachments/assets/b9c36b65-ae90-434c-96f9-42e5e483eb0c" />
> <img width="1248" height="785" alt="Captura de tela 2025-11-01 215958" src="https://github.com/user-attachments/assets/577fd7a9-f123-47e4-bcf7-8e7d63e4aa27" />
> <img width="1917" height="1019" alt="Captura de tela 2025-11-01 220121" src="https://github.com/user-attachments/assets/e4037c2a-b86a-4175-8776-af106f5d43b1" />
> <img width="1919" height="1018" alt="Captura de tela 2025-11-01 220218" src="https://github.com/user-attachments/assets/e4d1fad3-c377-4098-9767-22d797f44e20" />

> ---
> 
> ### 🔹 Consulta 1: Todos os dados
> ```sql
> SELECT * FROM DADOS_IRRIGACAO_RM566632;
> ```  
> <img width="1919" height="1008" alt="Captura de tela 2025-11-01 220531" src="https://github.com/user-attachments/assets/a316173d-8dc9-4ec7-a7bc-c09a1502a4e4" />

> 
> ---
> 
> ### 🔹 Consulta 2: Temperatura média
> ```sql
> SELECT AVG(temperatura) AS temp_media 
> FROM DADOS_IRRIGACAO_RM566632;
> ```  
> **Resultado:** 28.31°C – dentro da faixa ideal para cultivo de tomate (25-32°C).  
> <img width="1919" height="997" alt="Captura de tela 2025-11-01 220726" src="https://github.com/user-attachments/assets/63bf4eef-7bb9-4748-ae47-3e9af48b6bbd" />

> 
> ---
> 
> ### 🔹 Consulta 3: Bomba ligada
> ```sql
> SELECT timestamp, temperatura, umidade 
> FROM DADOS_IRRIGACAO_RM566632 
> WHERE bomba_ativa = 1;
> ```  
> **Análise:** A bomba foi ativada quando todos os nutrientes estavam presentes e a umidade estava baixa (56.8%), conforme a lógica programada.  
> <img width="1919" height="995" alt="Captura de tela 2025-11-01 220844" src="https://github.com/user-attachments/assets/83a942fc-6d8f-49b4-8571-d23a4e349931" />

> 
> ---
> 
> ### 🔹 Consulta 4: Umidade crítica (<60%)
> ```sql
> SELECT timestamp, umidade 
> FROM DADOS_IRRIGACAO_RM566632 
> WHERE umidade < 60;
> ```  
> **Análise:** Registros indicam períodos onde o solo necessitava de irrigação urgente.  
> <img width="1919" height="1023" alt="Captura de tela 2025-11-01 220920" src="https://github.com/user-attachments/assets/36f4c5b4-2da8-455b-96c3-ae90c3777d2a" />

> 
> ---
> 
> ### 🔹 Consulta 5: Contagem por combinação de nutrientes (NPK)
> ```sql
> SELECT nitrogenio, fosforo, potassio, COUNT(*) AS total
> FROM DADOS_IRRIGACAO_RM566632
> GROUP BY nitrogenio, fosforo, potassio;
> ```  
> **Resultado:**  
> - (0,0,0): 1 registro – sistema iniciando  
> - (1,0,0): 2 registros – apenas Nitrogênio  
> - (1,1,0): 2 registros – N + P  
> - (1,1,1): 25 registros – todos nutrientes presentes  
> **Análise:** A maior parte do tempo (83%) o sistema operou com todos os nutrientes disponíveis.  
> <img width="1919" height="1014" alt="Captura de tela 2025-11-01 220945" src="https://github.com/user-attachments/assets/f779f529-1d8a-4329-8e91-8cf170c4243d" />

> 
> ---
> 
> ### 🔹 Consulta 6: pH ideal (6.0-6.8)
> ```sql
> SELECT timestamp, ph 
> FROM DADOS_IRRIGACAO_RM566632 
> WHERE ph BETWEEN 6.0 AND 6.8;
> ```  
> **Análise:** O pH manteve-se majoritariamente dentro da faixa adequada (6.0-6.8), garantindo condições ideais para absorção de nutrientes.  
> <img width="1919" height="1015" alt="Captura de tela 2025-11-01 221022" src="https://github.com/user-attachments/assets/fa4012f2-1852-468e-a2a2-570e5d8264be" />

> 
> ---
> 
> ## 📈 Resultados
> - 🌡️ **Temperatura:** 26.9°C - 29.8°C → ✅ Ideal  
> - 💧 **Umidade do Solo:** 43.8% - 69.1% → ⚠️ Variável, atenção irrigação  
> - 🧪 **pH:** 5.9 - 6.6 → ✅ Dentro do esperado  
> - 🌱 **Nutrientes (NPK):** 83% do tempo disponíveis → ✅ Bom  
> - 💦 **Bomba:** 1 ativação → ✅ Funciona conforme lógica programada
> 
> ---
> 
> ## 🎥 Vídeo Demonstrativo
> [Link para demonstração](https://youtu.be/SEU_LINK_AQUI) – mostra **importação, consultas e análise dos dados**.
> 
> ---
> 
> ## 👤 Autora
> **Luana Brito da Silva**  
> RM: 566632 | Curso: Inteligência Artificial - FIAP

