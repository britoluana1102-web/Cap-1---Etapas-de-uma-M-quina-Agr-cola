# Cap-1---Etapas-de-uma-M-quina-Agricola
🌾 Fase 3 - Banco de Dados Oracle - Sistema de Irrigação Inteligente

📋 Sobre o Projeto

Este projeto faz parte da Fase 3 do PBL da FarmTech Solutions, focado em soluções de Agricultura 4.0. O objetivo é armazenar os dados do Sistema de Irrigação Inteligente com ESP32 em um banco de dados Oracle e realizar consultas SQL para análise.

🔧 Tecnologias

Oracle SQL Developer & Database

CSV para importação

SQL

GitHub

📁 Estrutura do Repositório
fase3/
├── dados/dados_sensores_farmtech.csv
├── prints/               # Prints das etapas importantes
├── README.md
└── video_demonstracao.txt

🚀 Passo a Passo com Imagens
1️⃣ Importação do CSV

Importação da tabela DADOS_IRRIGACAO_RM566632 com 30 registros.
<img width="1919" height="1018" alt="Captura de tela 2025-11-01 220218" src="https://github.com/user-attachments/assets/e18213b9-1924-46ea-a202-dadb17c00336" />


💻 Consultas SQL
Consulta 1: Todos os dados
SELECT * FROM DADOS_IRRIGACAO_RM566632;
<img width="1919" height="1008" alt="Captura de tela 2025-11-01 220531" src="https://github.com/user-attachments/assets/eacb5b67-b5b8-4ded-9730-bf58a54a7169" />


Consulta 2: Temperatura média
SELECT AVG(temperatura) AS temp_media 
FROM DADOS_IRRIGACAO_RM566632;
<img width="1919" height="997" alt="Captura de tela 2025-11-01 220726" src="https://github.com/user-attachments/assets/fc8c279b-0fef-4f78-a062-511522513766" />


Consulta 3: Bomba ligada
SELECT timestamp, temperatura, umidade 
FROM DADOS_IRRIGACAO_RM566632 
WHERE bomba_ativa = 1;
<img width="1919" height="995" alt="Captura de tela 2025-11-01 220844" src="https://github.com/user-attachments/assets/a7a79005-655f-4223-8754-daea89f9d749" />


Consulta 4: Umidade crítica (<60%)
SELECT timestamp, umidade 
FROM DADOS_IRRIGACAO_RM566632 
WHERE umidade < 60;
<img width="1919" height="1023" alt="Captura de tela 2025-11-01 220920" src="https://github.com/user-attachments/assets/bec06549-c5bc-40f9-be14-6ca49d097c6e" />


Consulta 5: Contagem por combinação de nutrientes
SELECT nitrogenio, fosforo, potassio, COUNT(*) AS total
FROM DADOS_IRRIGACAO_RM566632
GROUP BY nitrogenio, fosforo, potassio;
<img width="1919" height="1014" alt="Captura de tela 2025-11-01 220945" src="https://github.com/user-attachments/assets/e7b7e717-ace4-4673-8660-3bf21afdc7b4" />


Consulta 6: pH ideal (6.0-6.8)
SELECT timestamp, ph 
FROM DADOS_IRRIGACAO_RM566632 
WHERE ph BETWEEN 6.0 AND 6.8;
<img width="1919" height="1015" alt="Captura de tela 2025-11-01 221022" src="https://github.com/user-attachments/assets/e8bd6d86-1989-480c-82fa-3814c7c1d105" />


📈 Resultados

Temperatura: 26.9°C - 29.8°C → ✅ Ideal

Umidade: 43.8% - 69.1% → ⚠️ Variável, atenção irrigação

pH: 5.9 - 6.6 → ✅ Dentro do esperado

Nutrientes (NPK): 83% do tempo disponíveis → ✅ Bom

Bomba: 1 ativação → ✅ Funciona conforme lógica programada

🎥 Vídeo Demonstrativo

Link para demonstração
 – mostra importação, consultas e análise dos dados.

👤 Autora

Luana Brito da Silva – RM566632 – Curso de IA, FIAP
