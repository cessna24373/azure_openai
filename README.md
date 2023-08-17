# azure_openai

* https://zenn.dev/umi_mori/articles/langchain-cite-source  
* https://github.com/nohanaga/cognitive-search-vector-pr/blob/main/demo-python/code/azure-search-vector-python-sample.ipynb  
* https://github.com/Azure-Samples/jp-azureopenai-samples/tree/main/5.internal-document-search
* https://qiita.com/RyoJimmer/items/1e26448f088760822547
* https://qiita.com/yoshioterada/items/fddbc738cca9f24dac8b
* https://python.langchain.com/docs/modules/agents/how_to/agent_iter
* 

Summarize the following text into two concise bullet points:

Classify those company as either Tech ,Energy , Luxury Goods ,Investment.



container  app or web app service  ¥10/hour　→¥7200/month
gpt3.5 or 4 in azure openai api         ¥0.3/1000token

from diagrams import Cluster, Diagram
from diagrams.aws.compute import ECS
from diagrams.aws.database import ElastiCache, RDS
from diagrams.aws.network import ELB
from diagrams.azure.ml import CognitiveServices
from diagrams.azure.compute import AppServices
from diagrams.azure.web import Search
from diagrams.azure.database import CosmosDb
from diagrams.azure.database import BlobStorage

```python
with Diagram("Enterprise ChatBot", show=False) as diag:
    appService = AppServices("AppService")
    openai = CognitiveServices("OpenAI API")
    openai2 = CognitiveServices("OpenAI API")


    with Cluster("Event Workers"):
        with Cluster("Vector Store"):
            vstore=BlobStorage("Blob Storage")
        with Cluster("File Storage"):
            files=BlobStorage("Blob Storage")
        with Cluster("Embedding"):
            embed=CognitiveServices("OpenAI API")
        workers = [files >> embed >> vstore >> CosmosDb("faiss"),
           Search("bing API")]


    appService >> openai >> workers >> openai2
    appService << openai2
```

diag
design front 
