# GPT-RAG
```
pip install openai
```
## bing_search
크롤링을 사용하지 않고 검색 api를 사용하기 위해 Bing search api를 사용했습니다.    
Request 요청을 하기 위해 request 패키지를 import 해서 사용했습니다.    
사용자가 대화를 입력하면 `bing_search` 함수에서 Bing search api를 통해 request를 요청하고,    
그 결과를 json 형태로 반환하게 됩니다.    
반환된 json에서 필요한 부분인 snippet 부분들을 join해서 하나의 문자열로 만들어서 검색한 결과의 내용만 담게 됩니다.

## **generate_response**
검색한 결과의 내용만을 담은 `search_text`를 이용해 답변을 생성합니다.    
Openai의 api를 이용해 Text generation을 진행합니다.    
gpt-3.5-turbo 모델로 설정하고, content로 들어가는 것은 이전에 생성한 `search_text`가 들어가게 됩니다.    
이때, 주피터노트북으로 실행할 경우 `search_text`에는 이전에 답변했던 내용도 포함되어 있습니다.    
생성한 텍스트를 output으로 반환합니다.    

## 출력
1. 사용자가 입력한 질문을 출력합니다.    
2. 사용자의 질문에 대한 답을 output으로 출력합니다.    
    1. bing_search    
        질문을 bing search api를 이용해 검색한 결과를 반환한 내용을 토대로    
    2. generate_response    
        openai의 text generation model을 통해 답변을 만들어 반환합니다.    
        
----
추가) 기존에서 주피터노트북에서 실습할 때에는, 이전에 대화했던 내용을 기억하기 위해서 대화 컨텍스트에 질문과 응답 이력을 추가하는 것을 넣어서 사용했습니다.( `dialogue_history` )
