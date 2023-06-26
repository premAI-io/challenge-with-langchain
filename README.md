# Prem Challenge x LangChain

### Overview

Prem Labs aims to foster an ecosystem of privacy-preserving applications. We are excited to announce this challenge to incentivize the developers community to build innovative applications, services and solution that put users pricacy first. 

Teams participating at the challenge  will leverage Prem to deploy AI models and services on-premise. An important requirement is that the submitted applications shouldn't depend on centralized APIs at any point of their stack. 

### What

🛠 Teams participating in the challenge will develop Mobile, desktop, or web applications using one or many Prem AI services. Self-hosted AI models provide several benefits, including efficiency, cost optimization, and privacy.

To learn more about the challenge and review some reference implementations, head over to our basic tutorial to get up to speed with [Prem](README.md#getting-started--tutorial).

### About Prem

Prem provides a unified environment to develop AI applications and deploy AI models on your infrastructure. Abstracting away all technical complexities for AI deployment and ushering in a new era of privacy-centric AI applications — users can retain control and ownership of their models.

### When

📆 19th of June - 10th of July

### Where

🌍 Anywhere, Virtual

### How many?

🚶🚶🚶 Both solo and team accepted

### Prizes

Judges will shortlist and reward 3 of the best application submitted. 
💰Up to $ 10,000+ will be awarded at the final selected projects.

## Submission Requirements

To qualify for the challenge, your application should: 

1. **Open Source Github Repository** As Prem is open-source from the start. Also, apps and services MUST be open-source in all of their parts.
2. **Use Prem Services** From your local machine in development to production remote servers with the same interface, API, and services.
3. **Don't Log User Data on your server or third parties** No centralized API at any point of the stack! Your users want you to keep your data private!

### Judging Criteria

1. **Prompt utilization** We all know open-source models are not there yet, like OpenAI with powerful GPUs at their disposal: from constraints, humans can leverage their
creativity to produce unexpected results. Be smart at prompting.
2. **Commodity Hardware** If we want to bring the benefits of AI to billions of people in the global south without locking them in the Big Brother sight, we must work around it and make sure anyone can afford to buy computing resources. Run your apps on cheap VPS without GPU or very inexpensive ones.
3. **Composability** Combine all Prem services: LLMs, Diffusers, Embedding, and Vector stores.
4. **Production Status** How polished is your application? Can my grandma use it?

### Submission Process

**30th of June - BEFORE 6 PM UTC** [google form link](https://forms.gle/SHpQE1JtdSJAwo9S8)

Show some love to the [Prem App on Github](https://github.com/premAI-io/prem-app)

Follow us on Twitter - https://twitter.com/premai_io

# Getting Started / Tutorial

You can run Prem in two different ways:

- MacOS: go to https://premai.io and download Prem App.
- Server: run the installer script: `wget -q https://get.prem.ninja/install.sh -O install.sh; sudo bash ./install.sh`

### Run the services in the GUI

When the UI is up and running, you can see all the services available. With just one click you can download the service you are interested in. In the background, the docker image associated with the service will be downloaded based on your hardware requirements. 

![DownloadVicuna](https://github.com/premAI-io/llms-in-production-hackathon/assets/29598954/eb711c2a-2f67-46ad-af9f-b4afa05fcd12)

While waiting for the download to be completed, read more about the service, in the detail view. Just click on the card and you will be redirected to the service page. Each service page is packaged with some general info as well as complete documentation giving more details into the model exposed. When the download has been completed, just click on `Open` and the service will start. You can interact with the service from the playground or from APIs.

![StartVicuna](https://github.com/premAI-io/llms-in-production-hackathon/assets/29598954/3e225284-6e72-47be-b394-7956ee19cfc6)

You can check the port on which the service is running from the service detail view.

![RunningPort2](https://github.com/premAI-io/llms-in-production-hackathon/assets/29598954/e0fb120e-37cd-41e8-8329-ab8a38724308)

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
