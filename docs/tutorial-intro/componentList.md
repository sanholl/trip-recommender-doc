---
sidebar_position: 2
---

# 구조

```javascript
// index.d.ts
declare module 'trip-recommender' {
  ...
  export const ChatResponse: React.FC<ChatResponseProps>;
  export const SelectList: React.FC<SelectListProps>;
  export const RecommendationList: React.FC<RecommendationListProps>;
  export const ChatLoading: React.FC;
  export const Error: React.FC<ErrorProps>;
}
```




# 타입

```javascript
export interface ChatResponseProps {
  keyword: string;
  openAiKey: string;
}
export interface TripActivity {
  placeType: string;
  name: string;
  description: string;
  location: string;
  recommendedMenu?: string;
  link: string;
}
export interface RecommendationType {
  tripType: string;
  tripStyle: string;
  tripActivities: TripActivity[];
}
export interface RecommendationListProps {
  recommendation: RecommendationType;
}
export interface SelectListProps {
  onSelection: (who: string[], interest: string[]) => void;
}
export interface ChatResponseType {
  destination: string;
  recommendation: RecommendationType;
}

export interface ErrorProps {
  message: string;
}
```





### ChatResponse

선택된 장소, 위치와 관련되어 ai의 여행 추천을 보여주는 컴포넌트

```javascript
<ChatResponse
  keyword={keyword}
  openAiKey={OPEN_AI_KEY}
/>
```

#### Props

| 이름        | 설명                            | 타입   | 기타 |
| ----------- | ------------------------------- | ------ | ---- |
| `keyword`   | 여행 추천에 사용될 검색 keyword | String |      |
| `openAiKey` | open ai에서 발급받은 secret key | String |      |





### SelectList

사용자의 요구 조건을 최대한 근접한 답변을 내놓기 위한 추가 선택을 위한 옵션들을 보여주는 컴포넌트

```javascript
<SelectList onSelection={handleSelection} />
```

#### Props

| 이름              | 설명                             | 타입            | 기타 |
| ----------------- | -------------------------------- | --------------- | ---- |
| `handleSelection` | 선택되는 추가 옵션을 다루는 함수 | SelectListProps |      |

#### 예시
<img src="/img/selectList.png" width="100%" />






### RecommendationList

open ai의 응답 결과 값을 이용하여 `추천 일정` 을 보여주는 컴포넌트

```javascript
<RecommendationList response={response} />
```

#### Props

| 이름       | 설명                       | 타입             | 기타 |
| ---------- | -------------------------- | ---------------- | ---- |
| `response` | open ai의 JSON 형태의 응답 | ChatResponseType |      |

#### 예시
<img src="/img/recommendationList.png" width="100%" />






### ChatLoading

ai 답변이 오기전 로딩 화면

```javascript
<ChatLoading />
```

#### 예시
<img src="/img/loading.png" width="100%" />






### Error

error에 대한 화면을 보여주는 컴포넌트

```javascript
<Error message={message} />
```

#### Props

| 이름       | 설명                       | 타입             | 기타 |
| ---------- | -------------------------- | ---------------- | ---- |
| `message` | error 메세지 | string |      |

#### 예시

<img src="/img/error.png" width="100%" />