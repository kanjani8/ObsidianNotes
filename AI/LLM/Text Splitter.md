### RecursiveCharacterTextSplitter

 재귀적으로 텍스트를 분할합니다. 
 먼저 큰 단위(예: 문단)로 텍스트를 분할하고, 필요하다면 더 작은 단위(예: 문장)로 재귀적으로 분할하여 지정된 최대 길이를 넘지 않도록 합니다. 
 이 방법은 ==의미 단위로 텍스트를 나누어야 하는 경우==에 유용합니다.

**특징:**

- **재귀적 접근 방식:** 큰 단위에서 작은 단위로 내려가며 텍스트를 분할합니다.
- **의미 보존:** 문단, 문장 등의 의미 단위를 최대한 보존하려고 합니다.
- **가변 길이:** 청크의 길이가 유연하며, 최대 길이를 초과하지 않도록 조정됩니다.

**사용 예시:**
```
from langchain.text_splitter import RecursiveCharacterTextSplitter

text = "Your long text goes here..."
splitter = RecursiveCharacterTextSplitter(chunk_size=100, chunk_overlap=20)
chunks = splitter.split_text(text)

```


#### CharacterTextSplitter

`CharacterTextSplitter`는 고정된 길이로 텍스트를 단순히 분할합니다. 지정된 문자 수만큼 텍스트를 나누며, 청크의 의미나 문장 경계 등을 고려하지 않습니다.

**특징:**

- **고정 길이:** 지정된 길이로 텍스트를 나눕니다.
- **의미 무시:** 문장이나 문단 경계를 고려하지 않습니다.

**사용 예시:**
```
from langchain.text_splitter import CharacterTextSplitter

text = "Your long text goes here..."
splitter = CharacterTextSplitter(chunk_size=100, chunk_overlap=20)
chunks = splitter.split_text(text)

```

#### NLTKTextSplitter

`NLTKTextSplitter`는 NLTK 라이브러리를 사용하여 텍스트를 문장 단위로 분할합니다. 이 Splitter는 문장 경계를 인식하고, 문장 단위로 텍스트를 나누는 데 주로 사용됩니다.

**특징:**

- **문장 단위 분할:** NLTK를 사용하여 문장 경계를 인식합니다.
- **자연어 처리:** 텍스트의 문법적 구조를 고려합니다.

**사용 예시:**
```
from langchain.text_splitter import NLTKTextSplitter

text = "Your long text goes here..."
splitter = NLTKTextSplitter()
chunks = splitter.split_text(text)
```
### 요약

- **RecursiveCharacterTextSplitter:** 재귀적으로 텍스트를 의미 단위로 분할하여 최대 길이를 초과하지 않도록 조정합니다.
- **CharacterTextSplitter:** 지정된 길이로 단순히 텍스트를 분할합니다.
- **NLTKTextSplitter:** NLTK를 사용하여 문장 단위로 텍스트를 분할합니다.

`RecursiveCharacterTextSplitter`는 텍스트의 의미를 보존하면서 최대한 길이를 맞추고자 할 때 유용하며, 다른 스플리터는 더 단순하거나 특정한 텍스트 단위를 분할하는 데 적합합니다.

4o