# Azure AI Search + Azure Storage Account

Este repositório documenta o processo de configuração e integração do **Azure AI Search** com um **Storage Account**, baseado no fluxo seguido durante a implementação.

## Introdução
O **Azure AI Search** é um serviço gerenciado de pesquisa em nuvem que permite indexar e buscar informações de diferentes fontes, incluindo o **Azure Blob Storage**. Essa ferramenta é amplamente utilizada para análise de documentos, sistemas de recomendação e pesquisa semântica em grandes volumes de dados.

---
## Passo a Passo para Configuração

### 1. Criar os Recursos no Azure

#### **Recursos Necessários:**
- **Azure AI Search**: Gerencia a indexação e consulta dos documentos.
- **Azure AI Services**: Fornece serviços de IA para enriquecer os dados.
- **Storage Account**: Armazena os documentos a serem indexados.

### **Criar o Azure AI Search**
1. Acesse o [Portal do Azure](https://portal.azure.com/).
2. Clique em **+ Criar um recurso** e procure por **Azure AI Search**.
3. Configure com os seguintes valores:
   - **Subscription**: Sua assinatura do Azure.
   - **Resource group**: Selecione ou crie um novo.
   - **Service name**: Nome único.
   - **Location**: Escolha uma região disponível (Ex.: East US 2).
   - **Pricing tier**: Basic.
4. Clique em **Review + Create** e, após a validação, selecione **Create**.

### **Criar o Azure AI Services**
1. No Portal do Azure, clique em **+ Criar um recurso** e procure por **Azure AI Services**.
2. Configure com os seguintes valores:
   - **Subscription**: Sua assinatura do Azure.
   - **Resource group**: O mesmo do Azure AI Search.
   - **Region**: Mesma localização do Azure AI Search.
   - **Name**: Nome único.
   - **Pricing tier**: Standard S0.
3. Clique em **Review + Create** e, após a validação, selecione **Create**.

### **Criar o Storage Account**
1. No Portal do Azure, clique em **+ Criar um recurso** e procure por **Storage Account**.
2. Configure com os seguintes valores:
   - **Subscription**: Sua assinatura do Azure.
   - **Resource group**: O mesmo do Azure AI Search e Azure AI Services.
   - **Storage account name**: Nome único.
   - **Location**: Qualquer localização disponível.
   - **Performance**: Standard.
   - **Redundancy**: Locally Redundant Storage (LRS).
3. Clique em **Review + Create** e, após a validação, selecione **Create**.
4. No menu esquerdo do Storage Account, acesse **Configuração** e habilite **Allow Blob anonymous access**.
5. Salve as alterações.

---
### 2. Fazer Upload dos Documentos no Storage
1. No menu esquerdo do Storage Account, selecione **Containers**.
2. Clique em **+ Container** e defina:
   - **Name**: coffee-reviews.
   - **Public access level**: Container (anonymous read access for containers and blobs).
3. Clique em **Create**.
4. Baixe os arquivos de exemplo de [coffee reviews](https://aka.ms/mslearn-coffee-reviews) e extraia-os para uma pasta local.
5. No Portal do Azure, selecione o container **coffee-reviews** e clique em **Upload**.
6. Selecione todos os arquivos extraídos e clique em **Upload**.

---
### 3. Indexar os Documentos com Azure AI Search
1. Acesse o **Azure AI Search** no Portal do Azure.
2. Na página **Overview**, clique em **Import data**.
3. Configure os seguintes valores:
   - **Data Source**: Azure Blob Storage.
   - **Data source name**: coffee-customer-data.
   - **Data to extract**: Content and metadata.
   - **Parsing mode**: Default.
   - **Connection string**: Escolha a conexão existente e selecione seu **Storage Account**.
   - **Container name**: Preenchido automaticamente após a conexão.
   - **Blob folder**: Deixe em branco.
   - **Description**: Reviews for Fourth Coffee shops.
4. Clique em **Next** e finalize a importação.

---
## Insights e Possibilidades
A integração do **Azure AI Search** com o **Storage Account** permite:
- **Busca Rápida e Eficiente**: Indexa grandes volumes de documentos automaticamente.
- **Análise de Conteúdo**: Extração de informações de arquivos PDF, Word, JSON, etc.
- **Aplicabilidade em Chatbots**: Integração com IA para responder perguntas sobre documentos.
- **Filtros Avançados**: Permite buscas por metadados dos arquivos.

---
## Aprendizados Adquiridos
Durante essa implementação, alguns aprendizados importantes foram:
1. **Automatização da Indexação**: O indexador pode ser criado automaticamente via portal.
2. **Uso de AI Services**: Enriquecimento de dados com IA melhora a relevância dos resultados.
3. **Segurança dos Dados**: Configurar permissões adequadas para acesso ao Storage Account.

---
## Conclusão
A utilização do **Azure AI Search** para indexação de documentos no **Azure Storage Account** é uma solução poderosa para pesquisa rápida e eficiente. Esse conhecimento pode ser aplicado em diversas áreas, como automação de análise de documentos, chatbots inteligentes e sistemas de recomendação.

Caso tenha alguma dúvida ou sugestão, fique à vontade para contribuir! 🚀
