# Marketit 채용 과제

이 프로젝트는 [Create React App](https://github.com/facebook/create-react-app) (template typescript)을 통해 생성되었습니다.

## 개요

[HackerNews](https://github.com/HackerNews/API)의 공개 API 를 사용하여 article의 제목 목록을 보여주고, 제목을 클릭하여 전체 내용을 볼 수 있는 페이지를 구현합니다.\
이 Repository를 [Fork](https://github.com/marketit/marketit-assignment/fork)하여 작업한 후, 완료되었음을 recruit@marketit.io 에 알려주세요.\
자세한 내용은 아래 요구사항과 API 명세를 확인해주세요.

## 요구사항

### `필수`

1. 첫 화면에 story 제목이 리스트 형태로 노출되어야 합니다.
2. 제목을 클릭하면 story의 상세내용(제목, 작성자,댓글 목록)을 확인 할 수 있어야 합니다. 댓글의 댓글은 포함하지 않아도 됩니다. (Modal, Page 등 형식은 무관합니다.)

### `선택`

1. story 리스트를 최신순으로 정렬합니다.
2. story 리스트에 pagination을 적용합니다.
3. story 상세 내용에 보다 많은 정보를 보여줍니다(API 참고)
4. 모든 depth의 댓글을 보여줍니다.

### `참고`

1. 프로젝트의 구조 변경, 파일 생성 및 삭제, 라이브러리 설치 등은 모두 자유입니다.
2. 페이지의 심미성은 평가기준에 포함되지 않습니다.

## API Sepc

### Top Stories

story의 목록을 가져옵니다.\
첫 화면에 렌더링하는 데이터는 이 API를 사용하세요.\
\
Up to 500 top and new stories are at `/v0/topstories`

Example: https://hacker-news.firebaseio.com/v0/topstories.json?print=pretty

```javascript
[ 9129911, 9129199, 9127761, 9128141, 9128264, 9127792, 9129248, 9127092, 9128367, ..., 9038733 ]
```

### Items

id를 통해 각 item (story | comment)의 상세 정보를 가져옵니다.\
\
Stories, comments, jobs, Ask HNs and even polls are just items. They're identified by their ids, which are unique integers, and live under `/v0/item/<id>`.

All items have some of the following properties, with required properties in bold:

| Field       | Description                                                                        |
| ----------- | ---------------------------------------------------------------------------------- |
| **id**      | The item's unique id.                                                              |
| deleted     | `true` if the item is deleted.                                                     |
| type        | The type of item. One of "job", "story", "comment", "poll", or "pollopt".          |
| by          | The username of the item's author.                                                 |
| time        | Creation date of the item, in [Unix Time](http://en.wikipedia.org/wiki/Unix_time). |
| text        | The comment, story or poll text. HTML.                                             |
| dead        | `true` if the item is dead.                                                        |
| parent      | The comment's parent: either another comment or the relevant story.                |
| poll        | The pollopt's associated poll.                                                     |
| kids        | The ids of the item's comments, in ranked display order.                           |
| url         | The URL of the story.                                                              |
| score       | The story's score, or the votes for a pollopt.                                     |
| title       | The title of the story, poll or job. HTML.                                         |
| parts       | A list of related pollopts, in display order.                                      |
| descendants | In the case of stories or polls, the total comment count.                          |

For example, a story: https://hacker-news.firebaseio.com/v0/item/8863.json?print=pretty

```javascript
{
  "by" : "dhouston",
  "descendants" : 71,
  "id" : 8863,
  "kids" : [ 8952, 9224, 8917, 8884, 8887, 8943, 8869, 8958, 9005, 9671, 8940, 9067, 8908, 9055, 8865, 8881, 8872, 8873, 8955, 10403, 8903, 8928, 9125, 8998, 8901, 8902, 8907, 8894, 8878, 8870, 8980, 8934, 8876 ],
  "score" : 111,
  "time" : 1175714200,
  "title" : "My YC app: Dropbox - Throw away your USB drive",
  "type" : "story",
  "url" : "http://www.getdropbox.com/u/2/screencast.html"
}
```

comment: https://hacker-news.firebaseio.com/v0/item/2921983.json?print=pretty

```javascript
{
  "by" : "norvig",
  "id" : 2921983,
  "kids" : [ 2922097, 2922429, 2924562, 2922709, 2922573, 2922140, 2922141 ],
  "parent" : 2921506,
  "text" : "Aw shucks, guys ... you make me blush with your compliments.<p>Tell you what, Ill make a deal: I'll keep writing if you keep reading. K?",
  "time" : 1314211127,
  "type" : "comment"
}
```

## How to start

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `yarn build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

## Contact

위 과제와 관련하여 궁금한 사항이 있으실 경우 recruit@marketit.io 로 문의주시기 바랍니다.
