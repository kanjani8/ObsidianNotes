## 1. Basic of LLM Code

from langchain_openai import OpenAI
from langchain.chat_models import ChatOpenAI

llm = OpenAI()
chat = ChatOpenAI()

a = llm.predict("How many planets are there?")
b = chat.predict("how many planets are there?")

a, b

위 방법으로 각각 LLM과 Chat LLM을 불러와서 사용할 수 있다.
아무런 옵션을 집어넣지 않으면 openai에서 세팅된 기본 모델들을 불러온다.
해당 모델이 유료일 경우 .env의 key를 읽어내서 토큰을 소비한다.

chat llm의 경우 좀 더 대화형식, 즉 상호작용이 가능하며 맥락을 이해한다. 앞에서 했던 말을 기억하는 것이다.



chat = ChatOpenAI(
    temperature = 1 # how creative the model is. 0.1~1.
)
이런 식으로 모델의 창의성 등 값을 세팅할 수 있다.



## 2. Predict messages

from langchain.schema import HumanMessage, AIMessage, SystemMessage 

messages = [
	 SystemMessage(content="You are a geography expert. And you only reply in Japanese.", ),
	AIMessage(content="こんにちは、私はカンです。"),
	HumanMessage(content="what is the distance between Tokyo and Okinawa? and Also, what is your name?")
]

chat.predict_messages(messages)

How to make message constructors to predict messages
system message는 LLM을 세팅할 때 보내는 메시지이다.


## 3. Prompt Templates
Prompt template는 프롬프트 템플릿을 그냥 String으로 만드는데 비해
Chat prompt template은 프롬프트 템플릿을 messages = []로부터 만든다.
#### Prompt Template
from langchain.prompts import PromptTemplate

chat = ChatOpenAI(temperature = 1) 

template = PromptTemplate.from_template("what is the distance between {country_a} and {country_b}?")
prompt = template.format(country_a="Turkey", country_b="Japan")

chat.predict(prompt)

#### Chat Prompt Template

from langchain.prompts import ChatPromptTemplate

chat = ChatOpenAI(temperature = 1) 

template = ChatPromptTemplate.from_messages([
    ("system", "You are a geography expert. And you only reply in {language}."),
    ("ai", "こんにちは、私は{name}です。"),
    ("human", "what is the distance between {country_a} and {country_b}? and Also, what is your name?")
])
prompt =template.format_messages(
    language="Ukraine",
    name="Nedilya",
    country_a="Ukraine",
    country_b="Tokyo"
)

chat.predict_messages(prompt)

output:
	AIMessage(content='Відстань між Україною і Токіо складає близько 8 407 кілометрів. Мене звуть Неділя. Я відповідаю на ваші питання українською мовою. Якщо у вас є ще питання, не соромтеся питати.', response_metadata={'token_usage': {'completion_tokens': 115, 'prompt_tokens': 55, 'total_tokens': 170}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None}, id='run-a343977c-15fb-4fae-87e5-c9b9185f697f-0')