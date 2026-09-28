# 🏦 Desafio Criativo: Extraindo Insights de Feedbacks em Contas Digitais

Repositório desenvolvido como parte do **Desafio Criativo: Extraindo Insights do Feedback de Clientes Bancários**. O projeto documenta a concepção e a engenharia de um prompt estruturado para orientar modelos de IA a extrair dores, gargalos e oportunidades na jornada de **onboarding e abertura de contas digitais**.

---

## 📌 Visão Geral do Cenário

O processo de abertura de contas em instituições financeiras digitais costuma registrar altas taxas de abandono durante o fluxo de cadastro e validação de identidade (KYC). Este projeto propõe uma abordagem orientada a dados para categorizar comentários não estruturados de novos clientes, transformando reclamações e dúvidas em ações priorizadas para times de Produto, Design (UX/UI) e Operações.

---

## 🧩 Construção da Solução Passo a Passo

### 🧱 Passo 1: Definição da Intenção
* **Objetivo:** Analisar feedbacks de novos usuários sobre a jornada de abertura de conta digital e primeiro uso para mapear falhas no envio de documentos, motivos de recusa ou abandono e dificuldades no primeiro acesso.
* **Público-alvo:** Squads de Onboarding, Risco/Compliance e Growth/Product Operations.
* **Decisão apoiada:** Otimização do funil cadastral, redução da taxa de rejeição de documentos e aceleração da ativação da conta.
* **Formato de entrega:** Resumo executivo, matriz de atrito em tabela e top 3 recomendações priorizadas.
* **Critério de sucesso:** Mapeamento preciso das etapas de maior fricção baseado puramente em fatos relatados, gerando soluções viáveis para engenharia e design.

---

### 🧱 Passo 2: Contexto e Restrições
* **Contexto dos dados:** Feedbacks colhidos via canais de suporte in-app, lojas de aplicativos (Google Play Store e Apple App Store) e plataformas de defesa do consumidor.
* **Campos considerados:** `lead_id` (anonimizado), canal de origem, sistema operacional/versão do app, etapa relatada, nota de avaliação (1 a 5) e transcrição do comentário.
* **Critérios de classificação:** Etapa da jornada cadastral, severidade do atrito (Crítico, Médio, Baixo) e sentimento do cliente.
* **Governança e Restrições (LGPD):**
  * Restrição estrita aos dados fornecidos (sem alucinações ou extrapolações estatísticas).
  * Mascaramento e censura imediata de dados pessoais sensíveis (PII): CPF, nomes, fotos, telefones e e-mails.
  * Menção explícita de inconclusividade quando o comentário for genérico.
  * Tom estritamente executivo e voltado à tomada de decisão de produto.

---

## 🚀 Prompt Final Estruturado (Passo 3)

```text
Atue como Lead Product Manager e Especialista em Experiência do Cliente (CX) focado em Contas Digitais e Onboarding Bancário.

Sua tarefa é analisar feedbacks de clientes sobre o processo de abertura de conta digital, verificação de identidade (KYC) e primeiros acessos, identificando principais pontos de atrito, causas de abandono e oportunidades de otimização de fluxo.

Contexto:
Os insights gerados serão utilizados pelas squads de Onboarding, Risco/Compliance e Produto para diminuir a taxa de abandono cadastral, aprimorar a usabilidade do app e acelerar a ativação da conta digital pelos novos correntistas.

Dados disponíveis por entrada:
- ID anonimizado do cliente
- Canal de origem (ex.: Play Store, App Store, Chat de Suporte, Reclame Aqui)
- Sistema operacional e versão do aplicativo
- Etapa relatada no comentário
- Nota de avaliação (1 a 5)
- Texto do feedback

Instruções de análise:
1. Agrupe os feedbacks de acordo com a etapa da jornada de abertura de conta:
   - Captura e validação de documentos (RG/CNH);
   - Prova de vida / Selfie biométrica;
   - Tempo de análise cadastral e comunicação de aprovação/recusa;
   - Primeiro acesso e configuração de segurança (senha, chave Pix, biometria).
2. Classifique o sentimento geral e o nível de atrito (Crítico, Médio, Baixo) em cada grupo.
3. Extraia padrões de problemas técnicos ou de design (ex.: iluminação na foto do documento, lentidão na resposta do backend, mensagens de erro genéricas), citando trechos curtos dos comentários como evidência factual.
4. Formule recomendações práticas divididas entre melhorias de UX/UI e ajustes de regras de negócio ou operacionais.

Formato da resposta:
- Resumo Executivo: Visão geral concisa (até 5 linhas) sobre os maiores gargalos na adesão de novos clientes.
- Matriz de Atrito no Onboarding (Tabela):
  | Etapa da Jornada | Nível de Criticidade | Sentimento | Evidência (Trecho do Comentário) | Problema Identificado | Recomendação Prática (UX / Processo) |
- Recomendações Prioritárias: Top 3 ações com maior potencial de destravar o funil de abertura e ativação de contas.

Restrições e Governança de Dados:
- Utilize estritamente os comentários fornecidos; não suponha taxas ou dados estatísticos sem respaldo no texto.
- Cumpra os princípios da LGPD: remova qualquer dado identificável (CPF, nomes completos, telefones, números de protocolo).
- Se algum relato tiver dados insuficientes para apontar a causa exata, aponte a limitação com clareza.
- Empregue tom executivo, objetivo e orientado a métricas de produto (conversão e ativação).
