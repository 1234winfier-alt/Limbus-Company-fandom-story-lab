# Limbus-Company-fandom-story-lab
A space for Limbus Company fans to write novels and create stories together.
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>림버스 컴퍼니 팬덤 글 창작소</title>
    <style>
        :root {
            --bg-color: #0b0b0e;
            --card-bg: #141419;
            --card-hover: #1c1c24;
            --accent-color: #cc2929;
            --accent-hover: #e63939;
            --text-main: #f0f0f5;
            --text-sub: #9999a6;
            --border-color: #262633;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Noto Sans KR', -apple-system, BlinkMacSystemFont, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        /* 상단 네비게이션바 */
        header {
            background-color: var(--card-bg);
            border-bottom: 1px solid var(--border-color);
            padding: 0.8rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 1.2rem;
            font-weight: 800;
            color: var(--accent-color);
            text-decoration: none;
            letter-spacing: -0.5px;
        }

        .auth-nav button, .user-nav button {
            background: transparent;
            border: 1px solid var(--border-color);
            color: var(--text-main);
            padding: 0.4rem 0.9rem;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.2s;
            margin-left: 0.4rem;
        }

        .auth-nav button.btn-primary {
            background-color: var(--accent-color);
            border-color: var(--accent-color);
        }

        .auth-nav button:hover, .user-nav button:hover {
            border-color: var(--accent-color);
            opacity: 0.9;
        }

        /* 본문 레이아웃 (한 화면에 밀도 있게 모인 구조) */
        main {
            flex: 1;
            max-width: 1000px;
            width: 100%;
            margin: 1.5rem auto;
            padding: 0 1rem;
            display: grid;
            grid-template-columns: 280px 1fr;
            gap: 1.5rem;
        }

        @media(max-width: 768px) {
            main {
                grid-template-columns: 1fr;
            }
        }

        /* 사이드바 (프로필 및 메뉴) */
        aside {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 1.2rem;
        }

        .profile-card h3 {
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
            color: #fff;
        }

        .profile-card p {
            font-size: 0.85rem;
            color: var(--text-sub);
            margin-bottom: 1rem;
        }

        /* 게시판 메인 영역 */
        .content-section {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 1.5rem;
            min-height: 400px;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            padding-bottom: 0.75rem;
            border-bottom: 1px solid var(--border-color);
        }

        .section-header h2 {
            font-size: 1.2rem;
            color: #fff;
        }

        .write-btn {
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.85rem;
        }

        .write-btn:hover {
            background-color: var(--accent-hover);
        }

        /* 게시글 목록 스타일 */
        .post-list {
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .post-item {
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            padding: 1rem;
            border-radius: 6px;
            cursor: pointer;
            transition: 0.2s;
        }

        .post-item:hover {
            border-color: var(--accent-color);
            background-color: var(--card-hover);
        }

        .post-title {
            font-size: 1rem;
            font-weight: bold;
            margin-bottom: 0.3rem;
            color: #fff;
        }

        .post-meta {
            font-size: 0.8rem;
            color: var(--text-sub);
            display: flex;
            gap: 1rem;
        }

        /* 모달 팝업 디자인 */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.75);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .modal-content {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            padding: 2rem;
            border-radius: 8px;
            width: 100%;
            max-width: 380px;
            position: relative;
        }

        .close-btn {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: none;
            border: none;
            color: var(--text-sub);
            font-size: 1.4rem;
            cursor: pointer;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.4rem;
            color: var(--text-sub);
            font-size: 0.85rem;
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 0.65rem;
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            border-radius: 4px;
            color: var(--text-main);
            font-size: 0.9rem;
        }

        .form-group textarea {
            resize: vertical;
            height: 120px;
        }

        .submit-btn {
            width: 100%;
            padding: 0.7rem;
            background-color: var(--accent-color);
            border: none;
            border-radius: 4px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            margin-top: 0.5rem;
        }

        .submit-btn:hover {
            background-color: var(--accent-hover);
        }
    </style>
</head>
<body>

    <!-- 상단 바 -->
    <header>
        <a href="#" class="logo">림버스 글 창작소</a>
        <div id="navContainer">
            <!-- 동적 렌더링 영역 -->
        </div>
    </header>

    <!-- 메인 컨테이너 -->
    <main>
        <!-- 사이드바 -->
        <aside>
            <div class="card profile-card" id="sideProfile">
                <!-- 로그인 상태에 따라 변경 -->
            </div>
            <div class="card">
                <h3 style="font-size: 1rem; margin-bottom: 0.5rem; color: #fff;">공지사항</h3>
                <p style="font-size: 0.85rem; color: var(--text-sub); line-height: 1.4;">
                    림버스 컴퍼니 팬픽션 및 자작 스토리를 자유롭게 공유하는 공간입니다. 닉네임과 비밀번호로 간편하게 가입하세요!
                </p>
            </div>
        </aside>

        <!-- 게시판 영역 -->
        <section class="content-section">
            <div class="section-header">
                <h2>창작 소설 게시판</h2>
                <button class="write-btn" onclick="openWriteModal()">글작성</button>
            </div>
            <div class="post-list" id="postList">
                <!-- 글 목록이 여기에 표시됩니다 -->
            </div>
        </section>
    </main>

    <!-- 로그인 모달 -->
    <div class="modal" id="loginModal">
        <div class="modal-content">
            <button class="close-btn" onclick="closeModal('loginModal')">&times;</button>
            <h2 style="font-size: 1.25rem; margin-bottom: 1.2rem;">로그인</h2>
            <form onsubmit="handleLogin(event)">
                <div class="form-group">
                    <label>닉네임</label>
                    <input type="text" id="loginNick" required placeholder="닉네임 입력">
                </div>
                <div class="form-group">
                    <label>비밀번호</label>
                    <input type="password" id="loginPass" required placeholder="비밀번호 입력">
                </div>
                <button type="submit" class="submit-btn">로그인</button>
            </form>
        </div>
    </div>

    <!-- 회원가입 모달 -->
    <div class="modal" id="signupModal">
        <div class="modal-content">
            <button class="close-btn" onclick="closeModal('signupModal')">&times;</button>
            <h2 style="font-size: 1.25rem; margin-bottom: 1.
