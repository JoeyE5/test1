<!DOCTYPE html>
<html>
  <head>
    <title>Email Extractor</title>
    <style>
      /* CSS 스타일을 이곳에 작성하세요 */
    </style>
  </head>
  <body>
    <h1>Email Extractor</h1>
    <textarea id="inputText" rows="10" cols="50" placeholder="텍스트를 입력하세요..."></textarea>
    <button id="extractButton">추출</button>
    <h2>추출된 이메일:</h2>
    <ul id="emailList"></ul>

    <script>
      function extractEmails() {
        const inputText = document.getElementById("inputText").value;
        const regex = /\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}\b/g;
        const emails = inputText.match(regex);

        const emailList = document.getElementById("emailList");
        emailList.innerHTML = ""; // 기존의 목록 초기화

        if (emails) {
          emails.forEach((email) => {
            const li = document.createElement("li");
            li.innerText = email;
            emailList.appendChild(li);
          });
        } else {
          const li = document.createElement("li");
          li.innerText = "추출된 이메일이 없습니다.";
          emailList.appendChild(li);
        }
      }

      const extractButton = document.getElementById("extractButton");
      extractButton.addEventListener("click", extractEmails);
    </script>
  </body>
</html>
