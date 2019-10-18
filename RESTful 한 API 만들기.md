# RESTful 한 API 만들기

---

이 내용은 Roy T. Fielding 의 논문에 기초해 작성되었습니다.

1. Starting with the Null Style

   - Blank 부터 제약이나 제한 없이 시작하라.
   - 전체 시스템의 플로우를 생각하라.

   => 컴포넌트간에 서로 제한이 없어야 한다.

2. Client-Server

   - Client = a triggering process
   - Server = a reactive process
   - Clients make requests that trigger reactions from servers.
   - A client initiates activity at times of its choosing.
   - A server waits for requests to be made and then reacts to them.

   => A server is a non-terminating process and often provides service to more than one client.

   => The basic form of client-server does not contain how application state is partitioned between client and server components.

3. Stateless

   - Each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server.

   => Session state is therefore kept entirely on the client.