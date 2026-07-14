---
title: 'Home'
type: landing
sections:
  - block: hero
    content:
      title: "보이지 않는 곳에서 완벽한 흐름을 관리합니다."
      text: "마트 창고 매니저 이관용의 기록."
    design:
      css_id: hero
      spacing:
        padding: ['8rem', 0, '8rem', 0]

  - block: markdown
    content:
      title: "🙋 소개 (About)"
      text: "매일 마트로 들어오는 모든 물건의 시작과 끝을 책임지는 창고 매니저 이관용입니다. 정확한 분류와 철저한 재고 관리를 통해 매장의 완벽한 물류 흐름을 만드는 것을 제 최고의 보람으로 삼고 있습니다. 화려하게 드러나지는 않지만, 보이지 않는 곳에서의 꼼꼼함과 책임감이 마트의 하루를 움직인다고 믿습니다. 묵묵히 제 자리를 지키며 신뢰를 쌓아가는 보통사람의 성실한 기록을 이곳에 담아갑니다."
    design:
      css_id: about
      spacing:
        padding: ['5rem', 0, '5rem', 0]

  - block: collection
    content:
      title: "🗂️ 나의 일터 & 일상 기록 (블로그)"
      page_type: blog
      count: 3
      sort_by: Date
      sort_ascending: false
    design:
      css_id: blog
      view: card
      spacing:
        padding: ['5rem', 0, '5rem', 0]

  - block: markdown
    content:
      title: "💬 소통 게시판 (방명록)"
      text: |
        <div class="w-full max-w-xl mx-auto bg-white dark:bg-gray-800 p-6 rounded-lg shadow-md border border-gray-100 dark:border-gray-700">
          <p class="text-gray-600 dark:text-gray-300 text-center mb-6">
            오늘도 수고 많으셨습니다. 들러주신 동료분들, 지인분들의 따뜻한 한마디를 기다립니다.
          </p>
          
          <form id="guestbook-form" onsubmit="event.preventDefault(); submitComment();" class="space-y-4">
            <div>
              <label for="nickname" class="block text-sm font-semibold text-gray-700 dark:text-gray-300 mb-1">이름</label>
              <input type="text" id="nickname" required placeholder="이름을 입력해 주세요" class="w-full px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-md focus:ring-2 focus:ring-navy focus:border-navy dark:bg-gray-700 dark:text-white">
            </div>
            <div>
              <label for="message" class="block text-sm font-semibold text-gray-700 dark:text-gray-300 mb-1">메시지</label>
              <textarea id="message" rows="3" required placeholder="따뜻한 한마디를 남겨주세요" class="w-full px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-md focus:ring-2 focus:ring-navy focus:border-navy dark:bg-gray-700 dark:text-white"></textarea>
            </div>
            <button type="submit" class="w-full bg-navy hover:bg-navy-dark text-white font-semibold py-2 px-4 rounded-md transition duration-200 shadow">
              글 남기기
            </button>
          </form>

          <div class="mt-8 border-t border-gray-200 dark:border-gray-700 pt-6">
            <h4 class="font-bold text-gray-900 dark:text-white mb-4">방명록 목록</h4>
            <div id="comment-list" class="space-y-4">
              <!-- 댓글이 동적으로 추가되는 곳 -->
            </div>
          </div>
        </div>

        <script>
          function loadComments() {
            const comments = JSON.parse(localStorage.getItem('guestbook_comments') || '[]');
            const list = document.getElementById('comment-list');
            if (!list) return;
            
            if (comments.length === 0) {
              list.innerHTML = '<p class="text-gray-400 dark:text-gray-500 text-sm text-center py-4">첫 번째 방명록을 남겨주세요!</p>';
              return;
            }
            
            list.innerHTML = comments.map(c => `
              <div class="bg-gray-50 dark:bg-gray-900 p-4 rounded-md border border-gray-100 dark:border-gray-800 text-left">
                <div class="flex justify-between items-center mb-1">
                  <span class="font-semibold text-gray-800 dark:text-gray-200 text-sm">${c.name}</span>
                  <span class="text-gray-400 dark:text-gray-500 text-xs">${c.date}</span>
                </div>
                <p class="text-gray-600 dark:text-gray-300 text-sm whitespace-pre-line">${c.message}</p>
              </div>
            `).reverse().join('');
          }

          function submitComment() {
            const nameInput = document.getElementById('nickname');
            const msgInput = document.getElementById('message');
            if (!nameInput || !msgInput) return;
            
            const name = nameInput.value.trim();
            const message = msgInput.value.trim();
            if (!name || !message) return;
            
            const newComment = {
              name: name,
              message: message,
              date: new Date().toLocaleDateString('ko-KR', { year: 'numeric', month: 'long', day: 'numeric', hour: '2-digit', minute: '2-digit' })
            };
            
            const comments = JSON.parse(localStorage.getItem('guestbook_comments') || '[]');
            comments.push(newComment);
            localStorage.setItem('guestbook_comments', JSON.stringify(comments));
            
            nameInput.value = '';
            msgInput.value = '';
            loadComments();
          }

          // DOM 로드 시 실행
          document.addEventListener('DOMContentLoaded', loadComments);
          // 즉시 한 번 더 실행 (페이지 이동 시 대응)
          setTimeout(loadComments, 500);
        </script>
    design:
      css_id: guestbook
      spacing:
        padding: ['5rem', 0, '5rem', 0]

  - block: markdown
    content:
      title: "✉️ 연락처 (Contact)"
      text: |
        <div class="text-center space-y-4">
          <p class="text-lg text-gray-600 dark:text-gray-300">
            업무 협업 문의나 전하실 말씀은 아래 이메일로 연락 주시기 바랍니다.
          </p>
          <div class="mt-4">
            <a href="mailto:kwlee.logistics@gmail.com" class="inline-flex items-center gap-2 bg-navy hover:bg-navy-dark text-white px-6 py-3 rounded-md font-semibold transition duration-200 shadow">
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
              kwlee.logistics@gmail.com
            </a>
          </div>
          <p class="text-gray-400 text-xs mt-2">
            (추후 본인 이메일로 수정 가능)
          </p>
        </div>
    design:
      css_id: contact
      spacing:
        padding: ['5rem', 0, '5rem', 0]
---
