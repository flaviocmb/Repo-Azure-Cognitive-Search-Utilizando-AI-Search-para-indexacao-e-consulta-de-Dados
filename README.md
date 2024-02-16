# Repo: Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados
### Objetivo

Repositório criado para entregar o projeto final da etapa: Azure Cognitive Search - Utilizando AI Search para indexação e consulta de Dados.

Três **recursos** são importantes para esse experimento:

- Azure AI Search
- Azure AI services
- Storage account

# Requerimentos do projeto
### Como Entregar esse projeto?

Chegou a hora de você construir um portfólio ainda mais rico e impressionar futuros recrutadores, para isso é sempre importante mostrar os resultados do seu esforço e como você os obteve deixando claro o seu racional, para isso faça da seguinte maneira:

1. Crie um novo repositório no github com um nome a sua preferência
2. Crie um arquivo readme.md descrevendo o passo a passo para se configurar uma pesquisa, assim como seus insights, possibilidades de ferramentas que se beneficiam com esse tipo de ferramenta e aprendizados adquiridos durante o processo.
3. Compartilhe conosco o link desse repositório através do botão 'entregar projeto'

# Link útil

1. https://aka.ms/ai900-ai-search

# Crie um arquivo readme.md descrevendo o passo a passo para se configurar uma pesquisa, assim como seus insights, possibilidades de ferramentas que se beneficiam com esse tipo de ferramenta e aprendizados adquiridos durante o processo.

⭐️ A minha sugestão é deixar toda a plataforma em inglês ⭐️

### Passo a passo para se configurar uma pesquisa

* Criar um recurso Azure AI Search
* Criar um recurso Azure AI services
* Criar um Storage Account
* Adicionar documentos ao Azure Storage
* Indexar os documentos
* Consultar o índice
* Revisar o knowledge store

#### Crie um recuros Azure AI Search

1. Esteja logado no [Portal Azure](https://portal.azure.com).
2. Clique em **+ Create a resource**, procure e crie um **Azure AI Search** com as configurações abaixo:

	* **Subscription**: Your Azure subscription.
	* **Resource group**: Select or create a resource group with a unique name.
	* **Service name**: A unique name.
	* **Location**: Choose any available region.
	* **Pricing tier**: Basic.

| 2.1 | 2.2 | 2.3 | 2.4 |
|:--------:|:--------:|:--------:|:--------:|
|![Imagem 2](./imagens/imagem2.png)|![Imagem 3](./imagens/imagem3.png)|![Imagem 4](./imagens/imagem4.png)|![Imagem 5](./imagens/imagem5.png)|

#### Criar um recurso Azure AI services

3. Retorne ao início do [Portal Azure](https://portal.azure.com) e clique novamente em **+ Create a resource**, procure e crie um **Azure AI services** com as configurações abaixo:

	* **Subscription**: Your Azure subscription.
	* **Resource group**: The same resource group as your Azure AI Search resource.
	* **Region**: The same location as your Azure AI Search resource.
	* **Name**: A unique name.
	* **Pricing tier**: Standard S0.
	* **By checking this box I acknowledge that I have read and understood all the terms below**: Selected.

| 3.1 | 3.2 | 3.3 |
|:--------:|:--------:|:--------:|
|![Imagem 6](./imagens/imagem6.png)|![Imagem 7](./imagens/imagem7.png)|![Imagem 8](./imagens/imagem8.png)|

#### Criar um Storage Account

4. Retorne ao início do [Portal Azure](https://portal.azure.com) e clique novamente em **+ Create a resource**, procure e crie um **storage account** com as configurações abaixo:

	* **Subscription**: Your Azure subscription.
	* **Resource group**: The same resource group as your Azure AI Search and Azure AI services resources.
	* **Storage account name**: A unique name.
	* **Location**: Choose any available location.
	* **Performance**: Standard.
	* **Redundancy**: Locally redundant storage (LRS).

| 4.1 | 4.2 | 4.3 |
|:--------:|:--------:|:--------:|
|![Imagem 9](./imagens/imagem9.png)|![Imagem 10](./imagens/imagem10.png)|![Imagem 11](./imagens/imagem11.png)|

5. Após criar um **storage account**, no menu lateral esquerdo, acesse as configurações do seu storage account e altere a opção **Allow Blob anonymous access** para **Enabled** e salve. ⚠️

| 5.1 | 5.2 |
|:--------:|:--------:|
|![Imagem 12](./imagens/imagem12.png)|![Imagem 13](./imagens/imagem13.png)|

#### Adicionar documentos ao Azure Storage

6. Dentro do seu recurso **Azure Storage Account**, no menu lateral esquerdo, acesse **Containers**, selecione **+ Container**. Vai abrir um menu lateral à direita. Preencha as informações como fornecido abaixo:

* **Name**: coffee-reviews.
* **Public access level**: Container (anonymous read access for containers and blobs).
* **Advanced**: no changes.

| 6.1 | 6.2 |
|:--------:|:--------:|
|![Imagem 14](./imagens/imagem14.png)|![Imagem 15](./imagens/imagem15.png)|

7. Em uma nova janela do seu navegador, acesse esse [link](https://aka.ms/mslearn-coffee-reviews) para fazer o download dos arquivos de exemplo.

8. Ainda na sessão de **Containers**, acesse o container recém criado **coffee-reviews** e clique em **Upload**. Uma janela à direita se abrirá e você deverá selecionar os arquivos baixados e descompactados do passo anterior no seu computador.

| 8.1 | 8.2 | 8.3 | 8.4 |
|:--------:|:--------:|:--------:|:--------:|
|![Imagem 16](./imagens/imagem16.png)|![Imagem 17](./imagens/imagem17.png)|![Imagem 18](./imagens/imagem18.png)|![Imagem 19](./imagens/imagem19.png)|

9. Após isso, clique em Upload, dessa janela, para adicionar os documentos com as opiniões dos clientes para o container.

| 9.1 | 9.2 |
|:--------:|:--------:|
|![Imagem 20](./imagens/imagem20.png)|![Imagem 21](./imagens/imagem21.png)|

#### Indexar os documentos

Depois de armazenar os documentos, você poderá usar o **Azure AI Search** para extrair insights dos documentos. O portal do Azure fornece um *Import data wizard*. Com esse wizard, você pode criar automaticamente um index (índice) e um indexer (indexador) para fontes de dados suportadas. Você usará o wizard para criar um index e importar seus documentos de opiniões do armazenamento para o index do **Azure AI Search**.

10. No [Portal Azure](https://portal.azure.com), navegue até o recurso criado **Azure AI Search** e selecione o botão **Import data**.

| 10.1 |
|:--------:|
|![Imagem 22](./imagens/imagem22.png)|

11. Na guia **Connect to your data**, observe a lista em drop-down **Data Source**, selecione **Azure Blob Storage**. Complete as informações como mostrado abaixo:

	* **Data Source**: Azure Blob Storage
	* **Data source name**: coffee-customer-data
	* **Data to extract**: Content and metadata
	* **Parsing mode**: Default
	* **Connection string**: Select Choose an existing connection. Select your storage account, select the coffee-reviews container, and then click Select.
	* **Managed identity authentication**: None
	* **Container name**: this setting is auto-populated after you choose an existing connection.
	* **Blob folder**: Leave this blank.
	* **Description**: Reviews for Fourth Coffee shops.

| 11.1 | 11.2 | 11.3 | 11.4 |
|:--------:|:--------:|:--------:|:--------:|
|![Imagem 23](./imagens/imagem23.png)|![Imagem 24](./imagens/imagem24.png)|![Imagem 25](./imagens/imagem25.png)|![Imagem 26](./imagens/imagem26.png)|

12. Clique em **Next: Add cognitive skills (Optional)**.

| 12.1 |
|:--------:|
|![Imagem 27](./imagens/imagem27.png)|

13. Na seção **Attach Cognitive Services**, selecione o seu recuros Azure AI services.

| 13.1 |
|:--------:|
|![Imagem 28](./imagens/imagem28.png)|

14. Na seção **Add enrichments**:

	* Change the Skillset name to **coffee-skillset**.
	* Select the checkbox **Enable OCR and merge all text into merged_content field**.
	* Ensure that the Source data field is set to **merged_content**.
	* Change the Enrichment granularity level to **Pages (5000 character chunks)**.
	* Don’t select *Enable incremental enrichment*.
	* Select the following enriched fields: ⚠️ **(ver imagem 14.2)**.

| 14.1 | 14.2 |
|:--------:|:--------:|
|![Imagem 29](./imagens/imagem29.png)|![Imagem 30](./imagens/imagem30.png)|

15. Na seção **Save enrichments to a knowledge store**, selecione:

	* Image projections
		* ⚠️ Uma mensagem de alerta aparecerá em vermelho (ver imagem 15.2) perguntando sobre *Storage Account Connection String*, siga esses passos:
			1. Select **Choose an existing connection**. 
			2. Choose the storage account you created earlier.
			3. Click on **+ Container** to create a new container called knowledge-store with the privacy level set to Private, and select Create.
			4. Select the knowledge-store container, and then click Select at the bottom of the screen.
	* Documents
	* Pages
		* Key phrases
		* Entities
	* Image details
		* Image references

| 15.1 | 15.2 | 15.3 | 15.4 | 15.5 | 15.6 |
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
|![Imagem 31](./imagens/imagem31.png)|![Imagem 32](./imagens/imagem32.png)|![Imagem 33](./imagens/imagem33.png)|![Imagem 34](./imagens/imagem34.png)|![Imagem 35](./imagens/imagem35.png)|![Imagem 36](./imagens/imagem36.png)|

16. Ainda na seção **Save enrichments to a knowledge store**, selecione **Azure blob projections: Document**. Aparecerá o container recém criado knowledge-store, não altere esse nome mostrado.

| 16.1 |
|:--------:|
|![Imagem 37](./imagens/imagem37.png)|

17. Observe todas as configurações realizadas e selecione **Next: Customize target index**.

| 17.1 |
|:--------:|
|![Imagem 38](./imagens/imagem38.png)|

18. Na etapa seguinte, altere o **Index name** para **coffee-index**.

19. Garanta que o campo **Key** esteja configurado para **metadata_storage_path**. Deixe o **Suggester name** em branco e **Search mode** autopreenchido.

20. Observe com atenção as informações preenchidas das etapas 18 e 19 até aqui.

| 20.1 |
|:--------:|
|![Imagem 39](./imagens/imagem39.png)|

21. Selecione o checkbox **filterable** para todos os campos que já estão selecionados por padrão. Observe a imagem.

| 21.1 |
|:--------:|
|![Imagem 40](./imagens/imagem40.png)|

22. Clique em **Next: Create an indexer**.

23. Altere o *Indexer name* para **coffee-indexer**. Deixe o *Schedule* configurado para **Once**. Verifique se o **Base-64 Encode Keys** está selecionado em **Advanced options**. Clique em **Submit**.

| 23.1 |
|:--------:|
|![Imagem 41](./imagens/imagem41.png)|

24. Retorne à página do seu recurso **Azure AI Search**. No menu lateral esquerdo, abaixo de **Search Management**, selecione **Indexers**. Selecione o recém-criado **coffee-indexer**, aguarde até visualizar o **Status** indicar success ✅. Acesse o indexer **coffee-indexer** para visualizar os detalhes.

| 24.1 | 24.2 |
|:--------:|:--------:|
|![Imagem 42](./imagens/imagem42.png)|![Imagem 43](./imagens/imagem43.png)|

#### Consultar o índice

Use o **Search Explorer** para escrever e testar consultas. Você pode usar o **Search Explorer** para escrever consultas e revisar resultados em **JSON**.

25. Na página de Overview do recurso **Search service** que você criou, selecione **Search explorer** nas guias superiores.

| 25.1 |
|:--------:|
|![Imagem 43](./imagens/imagem43.png)|

26. Observando que o **coffee-index** é o index selecionado, altere a visualização de query view para **JSON view**, copie e cole o trecho de código abaixo e clique em **Search**.

```json
{
    "search": "*",
    "count": true
}
```

A consulta retorna todos os documentos, incluindo uma contagem de todos os documentos no campo **@odata.count**. Essa consulta está descrita no formato JSON.

| 26.1 | 26.2 | 26.3 | 26.4 |
|:--------:|:--------:|:--------:|:--------:|
|![Imagem 44](./imagens/imagem44.png)|![Imagem 45](./imagens/imagem45.png)|![Imagem 46](./imagens/imagem46.png)|![Imagem 47](./imagens/imagem47.png)|

27. Filtre por localidade. No campo **JSON query editor**, copie e cole o trecho de código abaixo e clique em **Search**.

```json
{
 "search": "locations:'Los Angeles'",
 "count": true
}
```

A consulta retorna filtros de review baseado na localidade **Los Angeles**. Observe o número 2 no campo **@odata.count**.

| 27.1 |
|:--------:|
|![Imagem 48](./imagens/imagem48.png)|

28. Agora filtre por **sentimento**. No campo **JSON query editor**, copie e cole o trecho de código abaixo e clique em **Search**.

```json
{
 "search": "sentiment:'negative'",
 "count": true
}
```

The query searches all the documents in the index and filters for reviews with a negative sentiment. You should see 1 in the @odata.count field.

A consulta retorna filtros de view com **sentimento negativo**. Observe o número 1 no campo **@odata.count**.

Veja como os resultados são classificados por **@search.score**. Essa é a pontuação atribuída pelo mecanismo de pesquisa para mostrar o quão próximos os resultados correspondem à consulta fornecida.

Observe os comentários negativos em **content**. Esses comentários estão associados aos **key phrases**. Isso ajuda a entender a causa dos reviews negativos.

| 28.1 |
|:--------:|
|![Imagem 49](./imagens/imagem49.png)|

#### Revisar o knowledge store

Quando você executou o *Import data wizard*, você criou um **knowledge store**. Dentro dele, você vai encontrar os dados enriquecidos extraídos pelas habilidades da IA que persistem na forma de projeções e tabelas.

29. No [Portal Azure](https://portal.azure.com), navegue de volta ao seu **Azure storage account**. No menu lateral esquerdo, selecione **Containers**, Clique no container **knowledge-store**.

| 29.1 |
|:--------:|
|![Imagem 50](./imagens/imagem50.png)|

30. Selecione qualquer pasta, depois clique no arquivo **objectprojection.json**. Selecione **Edit** e observe o JSON gerado para um dos documentos de review dos clientes direto do seu **Azure data store**.

| 30.1 | 30.2 | 30.3 | 30.4 |
|:--------:|:--------:|:--------:|:--------:|
|![Imagem 51](./imagens/imagem51.png)|![Imagem 52](./imagens/imagem52.png)|![Imagem 53](./imagens/imagem53.png)|![Imagem 54](./imagens/imagem54.png)|

31. Retorne ao seu **Storage account Containers** por meio do *breadcrumb* na guia superior esquerda da tela.

| 31.1 |
|:--------:|
|![Imagem 55](./imagens/imagem55.png)|

32. Selecione o container **coffee-skillset-image-projection**. Clique em qualquer arquivo e depois selecione qualquer arquivo .jpg. Clique em **Edit** para visualizar uma imagem armazenada no documento fornecido no **Azure data store**.

| 32.1 | 32.2 | 32.3 | 32.4 | 32.5 |
|:--------:|:--------:|:--------:|:--------:|:--------:|
|![Imagem 56](./imagens/imagem56.png)|![Imagem 57](./imagens/imagem57.png)|![Imagem 58](./imagens/imagem58.png)|![Imagem 59](./imagens/imagem59.png)|![Imagem 60](./imagens/imagem60.png)|

33. Retorne novamente ao seu **Storage account Containers**. Selecione **Storage browser** no menu lateral esquerdo, depois selecione **Tables**.

Há uma tabela para cada entidade no index. 

| 33.1 | 33.2 |
|:--------:|:--------:|
|![Imagem 61](./imagens/imagem61.png)|![Imagem 62](./imagens/imagem62.png)|

34. Selecione a tabela **coffeeSkillsetKeyPhrases**.

Observe os **key phrases** que o **knowledge store** conseguiu capturar do conteúdo das reviews. Muitos dos campos são keys, portanto você pode vincular as tabelas como um banco de dados relacional. O último campo mostra os **key phrases** que foram extraídos pelo skillset.

| 34.1 | 34.2 |
|:--------:|:--------:|
|![Imagem 63](./imagens/imagem63.png)|![Imagem 64](./imagens/imagem64.png)|

### Insights

### Possibilidades de ferramentas que se beneficiam com esse tipo de ferramenta

### Aprendizados adquiridos
