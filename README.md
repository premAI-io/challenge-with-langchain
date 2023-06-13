# LLMs in Production - Prem Hackathon

table of content

## Submission Requirements

1. Open Source Github Repository
2. Use Prem Services
3. Don't Log User Data on your server or third parties

## Judging Criterias

1. Prompt utilization
2. Commodity Hardware
3. Composability
4. Production Status

## Submission Process

google form link

## Getting Started / Tutorial

You can run Prem in two different ways:

- MacOS: go to https://premai.io and download Prem App.
- Server: run the installer script: `wget -q https://get.prem.ninja/install.sh -O install.sh; sudo bash ./install.sh`

### Run the services in the GUI

When the UI is up and running, you can see all the services available. With just one click you can download the service you are interested in. In the background, the docker image associated with the service will be downloaded based on your hardware requirements. 

![DownloadVicuna.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c0c27330-ead7-4f9f-bdae-b16ee06593dc/DownloadVicuna.gif)

While waiting for the download to be completed, read more about the service, in the detail view. Just click on the card and you will be redirected to the service page. Each service page is packaged with some general info as well as complete documentation giving more details into the model exposed. When the download has been completed, just click on `Open` and the service will start. You can interact with the service from the playground or from APIs.

![StartVicuna.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c97bf9ac-7cb8-46b9-ab41-c653b0544c98/StartVicuna.gif)

You can check the port on which the service is running from the service detail view.

![RunningPort.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37e90ebb-21ce-48e1-877d-26e3cf05bcfb/RunningPort.gif)

### Start Building Your App

Now that the service is running, you can connect to it at http://localhost:8111 and start building. Here is a simple snippet using Langchain to connect to the service.

```python
import os

from langchain.chat_models import ChatOpenAI
from langchain.schema import AIMessage, HumanMessage

os.environ["OPENAI_API_KEY"] = "random-string"

chat = ChatOpenAI(openai_api_base="http://localhost:8111/api/v1", max_tokens=128)

messages = [
    HumanMessage(content="Can you explain what is a large language model?")
]
chat(messages)

messages = [
    HumanMessage(content="Write me a story about a superstar.")
]
chat(messages)
```

You can find more examples at: https://github.com/premAI-io/prem-daemon/blob/main/resources/notebooks/
