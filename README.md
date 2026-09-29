# canhbaotingia.htm/
<!DOCTYPE html>
<html lang="vi" class="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cảnh Báo & Bóc Trần Tin Giả - Fact-Check Radar Pro</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            bg: '#f8fafc',
                            card: '#ffffff',
                            primary: '#0284c7',
                            secondary: '#6366f1',
                            alert: '#ef4444',
                            warning: '#f59e0b',
                            success: '#10b981',
                            text: '#0f172a',
                            muted: '#64748b'
                        }
                    }
                }
            }
        }
    </script>
    <!-- Tone.js for sound feedback -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/tone/14.8.49/Tone.min.js"></script>
    <!-- Canvas Confetti for winning game -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        .neumorphism-card {
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05), 0 8px 10px -6px rgba(0, 0, 0, 0.05);
            border: 1px solid rgba(226, 232, 240, 0.8);
            transition: all 0.3s ease;
        }
        .dark .neumorphism-card {
            background: #1e293b;
            border-color: #334155;
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.3);
        }
        .highlight-redflag {
            background-color: #fee2e2;
            color: #b91c1c;
            border-bottom: 2px solid #ef4444;
            padding: 0 4px;
            border-radius: 4px;
            font-weight: 600;
            cursor: pointer;
            display: inline-block;
            transition: background 0.2s;
        }
        .dark .highlight-redflag {
            background-color: #7f1d1d;
            color: #fca5a5;
            border-bottom-color: #f87171;
        }
        .highlight-redflag:hover {
            background-color: #fecaca;
        }
        .dark .highlight-redflag:hover {
            background-color: #991b1b;
        }
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .dark ::-webkit-scrollbar-thumb {
            background: #475569;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between bg-slate-50 text-slate-900 dark:bg-slate-950 dark:text-slate-100 selection:bg-sky-500 selection:text-white">

    <!-- Header -->
    <header class="w-full border-b border-slate-200 dark:border-slate-800 bg-white/80 dark:bg-slate-900/80 backdrop-blur-md sticky top-0 z-50 px-4 py-3">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-4">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-sky-500 to-indigo-600 flex items-center justify-center text-white font-extrabold text-xl shadow-md shadow-sky-500/20">
                    🛡️
                </div>
                <div>
                    <h1 class="font-extrabold text-lg sm:text-xl tracking-tight">
                        FACT-CHECK <span class="text-transparent bg-clip-text bg-gradient-to-r from-sky-500 to-indigo-600">RADAR PRO</span>
                    </h1>
                    <p class="text-xs text-slate-500 dark:text-slate-400">Hệ thống quét, cảnh báo và bóc trần tin giả thông minh</p>
                </div>
            </div>

            <!-- Navigation Tabs & Toggles -->
            <div class="flex flex-wrap items-center gap-2">
                <button onclick="switchTab('scanner')" id="nav-scanner" class="px-3.5 py-1.5 rounded-xl text-xs font-semibold bg-sky-500 text-white shadow-sm transition">
                    🔍 Quét Văn Bản
                </button>
                <button onclick="switchTab('library')" id="nav-library" class="px-3.5 py-1.5 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition">
                    📰 Thư Viện Tin Giả
                </button>
                <button onclick="switchTab('game')" id="nav-game" class="px-3.5 py-1.5 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition">
                    🎮 Game Bắt Sâu
                </button>
                <button onclick="switchTab('toolkit')" id="nav-toolkit" class="px-3.5 py-1.5 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition">
                    📚 Cẩm Nang 5 Bước
                </button>
                
                <div class="flex items-center gap-1 ml-2">
                    <button onclick="toggleSound()" class="px-3 py-1.5 rounded-xl bg-slate-100 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-xs text-sky-600 dark:text-sky-400 hover:bg-slate-200 dark:hover:bg-slate-700 transition flex items-center gap-1 font-medium" title="Bật/Tắt âm thanh">
                        🔊 <span id="soundStatus">Bật</span>
                    </button>
                    <button onclick="toggleDarkMode()" class="px-3 py-1.5 rounded-xl bg-slate-100 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-xs text-amber-500 hover:bg-slate-200 dark:hover:bg-slate-700 transition" title="Đổi giao diện Sáng/Tối">
                        🌓
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="flex-1 max-w-6xl w-full mx-auto p-4 sm:p-6 my-auto">

        <!-- TAB 1: SCANNER & HIGHLIGHTER -->
        <div id="tab-scanner" class="space-y-6">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                <!-- Left Input Panel -->
                <div class="lg:col-span-7 space-y-4">
                    <div class="p-6 rounded-3xl neumorphism-card bg-white space-y-4">
                        <div class="flex items-center justify-between">
                            <h2 class="text-lg font-bold flex items-center gap-2">
                                <span>✍️</span> Nhập hoặc Dán Văn Bản Cần Quét
                            </h2>
                            <button onclick="loadSampleText()" class="text-xs text-sky-600 dark:text-sky-400 font-semibold hover:underline bg-sky-50 dark:bg-sky-950/50 px-3 py-1.5 rounded-lg border border-sky-100 dark:border-sky-900">
                                Lấy tin mẫu nghi vấn
                            </button>
                        </div>
                        <p class="text-xs text-slate-500 dark:text-slate-400 leading-relaxed">
                            Dán bài viết mạng xã hội, tin nhắn Zalo/Facebook hoặc thông cáo bất kỳ để hệ thống quét từ ngữ giật gân, bẫy tâm lý và kích động cảm xúc.
                        </p>
                        
                        <textarea id="textInput" rows="7" class="w-full p-4 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-sm text-slate-800 dark:text-slate-100 focus:outline-none focus:border-sky-500 transition" placeholder="Ví dụ: CHẤN ĐỘNG! Bí mật động trời bị che giấu suốt 10 năm về thần dược trị dứt điểm ung thư..."></textarea>

                        <div class="flex items-center justify-between pt-2">
                            <button onclick="clearScanner()" class="px-4 py-2 rounded-xl text-xs font-medium text-slate-600 dark:text-slate-400 bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 dark:hover:bg-slate-700 transition">
                                Xóa nội dung
                            </button>
                            <button onclick="analyzeText()" class="px-6 py-2.5 rounded-xl bg-gradient-to-r from-sky-500 to-indigo-600 text-white font-semibold text-sm hover:opacity-95 transition shadow-md shadow-sky-500/20 flex items-center gap-2">
                                ⚡ Bắt Đầu Quét & Phân Tích
                            </button>
                        </div>
                    </div>

                    <!-- Highlighted Text Result View -->
                    <div id="resultBox" class="hidden p-6 rounded-3xl neumorphism-card bg-white space-y-4">
                        <div class="flex items-center justify-between">
                            <h3 class="font-bold flex items-center gap-2 text-sm sm:text-base">
                                🔦 Văn Bản Được Quét & Highlight Cảnh Báo:
                            </h3>
                            <button onclick="copyReport()" class="text-xs text-sky-600 dark:text-sky-400 font-semibold hover:underline bg-sky-50 dark:bg-sky-950 px-2.5 py-1 rounded border border-sky-100 dark:border-sky-900">
                                📋 Sao chép kết quả
                            </button>
                        </div>
                        <div id="highlightedOutput" class="p-4 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-sm text-slate-700 dark:text-slate-300 leading-relaxed whitespace-pre-wrap"></div>
                        <p class="text-[11px] text-slate-400 italic">
                            * Nhấn vào các từ được bôi đỏ để xem phân tích chi tiết vì sao cụm từ đó bị nghi ngờ.
                        </p>
                    </div>
                </div>

                <!-- Right Analysis & Score Panel -->
                <div class="lg:col-span-5 space-y-4">
                    <div class="p-6 rounded-3xl neumorphism-card bg-white space-y-6">
                        <h3 class="font-bold text-base flex items-center gap-2">
                            📊 Chỉ Số Rủi Ro Tin Giả (Risk Score)
                        </h3>

                        <!-- Score Gauge Display -->
                        <div class="flex flex-col items-center justify-center p-6 bg-slate-50 dark:bg-slate-900 rounded-2xl border border-slate-200 dark:border-slate-700">
                            <div id="riskScoreCircle" class="w-28 h-28 rounded-full border-8 border-slate-200 dark:border-slate-700 flex flex-col items-center justify-center text-center shadow-inner">
                                <span id="riskScoreNum" class="text-3xl font-extrabold text-slate-700 dark:text-slate-200">0%</span>
                                <span class="text-[10px] text-slate-400 uppercase tracking-wider font-semibold">Độ rủi ro</span>
                            </div>
                            <div id="riskLevelText" class="mt-4 text-sm font-bold text-slate-600 dark:text-slate-300 text-center">
                                Chưa có dữ liệu phân tích
                            </div>
                        </div>

                        <!-- Detected Red Flags Breakdown -->
                        <div class="space-y-3">
                            <h4 class="text-xs font-bold uppercase tracking-wider text-slate-500 dark:text-slate-400">
                                Các bẫy tâm lý & từ khóa phát hiện:
                            </h4>
                            <div id="redFlagsList" class="space-y-2 max-h-60 overflow-y-auto pr-1">
                                <div class="p-3 rounded-xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-xs text-slate-500 text-center">
                                    Chưa phát hiện từ khóa khả nghi nào.
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 2: VIRAL FAKE NEWS LIBRARY -->
        <div id="tab-library" class="hidden space-y-6">
            <div class="p-6 sm:p-8 rounded-3xl neumorphism-card bg-white">
                <div class="max-w-2xl mb-6">
                    <h2 class="text-xl sm:text-2xl font-extrabold mb-2">Thư Viện Tin Giả & Hoài Nghi Phổ Biến</h2>
                    <p class="text-slate-600 dark:text-slate-400 text-xs sm:text-sm leading-relaxed">
                        Khám phá các kịch bản tin giả lan truyền mạnh mẽ trên mạng xã hội và cách chúng thao túng tâm lý cộng đồng. Bấm <span class="text-sky-600 dark:text-sky-400 font-bold">"Thử nghiệm ngay vào bộ quét"</span> để kiểm tra lập tức!
                    </p>
                </div>

                <div id="fakeNewsCardsContainer" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
            </div>
        </div>

        <!-- TAB 3: FACT-CHECK GAME ("BẮT SÂU TIN GIẢ") -->
        <div id="tab-game" class="hidden space-y-6">
            <div class="p-6 sm:p-8 rounded-3xl neumorphism-card bg-white text-center space-y-6 max-w-2xl mx-auto">
                <div id="gameStartContainer" class="space-y-4 py-6">
                    <div class="text-5xl">🎮</div>
                    <h2 class="text-2xl font-extrabold">Thử Thách: Bắt Sâu Tin Giả</h2>
                    <p class="text-slate-600 dark:text-slate-400 text-sm leading-relaxed">
                        Kiểm tra độ tinh mắt và tư duy phản biện của bạn qua các tình huống thực tế. Hãy phân định đâu là tin chính thống và đâu là tin giả mạo!
                    </p>
                    <button onclick="startGame()" class="px-8 py-3 rounded-2xl bg-gradient-to-r from-sky-500 to-indigo-600 text-white font-bold text-sm hover:opacity-95 transition shadow-lg shadow-sky-500/25">
                        🚀 Bắt Đầu Thử Thách
                    </button>
                </div>

                <div id="gamePlayContainer" class="hidden space-y-6 text-left">
                    <div class="flex items-center justify-between text-xs font-semibold text-slate-500 dark:text-slate-400 border-b border-slate-100 dark:border-slate-800 pb-3">
                        <span>Câu hỏi <span id="gameCurrQ" class="text-sky-600 dark:text-sky-400 font-bold">1</span> / 5</span>
                        <span class="text-indigo-600 dark:text-indigo-400 font-bold">Điểm: <span id="gameScore">0</span></span>
                    </div>

                    <div id="gameQuestionText" class="text-base sm:text-lg font-bold leading-relaxed">
                        Đang tải câu hỏi...
                    </div>

                    <div id="gameOptionsList" class="grid grid-cols-1 gap-3"></div>

                    <div id="gameExplanationBox" class="hidden p-4 rounded-2xl bg-slate-900 text-slate-100 space-y-3">
                        <h4 id="gameExpTitle" class="font-bold text-sm text-emerald-400">Kết quả phân tích:</h4>
                        <p id="gameExpText" class="text-xs text-slate-300 leading-relaxed"></p>
                        <button onclick="nextGameQuestion()" class="px-5 py-2 rounded-xl bg-sky-500 text-white font-semibold text-xs hover:bg-sky-600 transition">
                            Tiếp tục →
                        </button>
                    </div>
                </div>

                <div id="gameResultContainer" class="hidden space-y-4 py-4">
                    <div class="text-5xl">🏆</div>
                    <h3 class="text-2xl font-extrabold">Hoàn Thành Thử Thách!</h3>
                    <p id="gameFinalSummary" class="text-slate-600 dark:text-slate-400 text-sm"></p>
                    <button onclick="resetGame()" class="px-6 py-2.5 rounded-xl bg-sky-500 text-white font-semibold text-sm hover:bg-sky-600 transition">
                        🔄 Chơi lại
                    </button>
                </div>
            </div>
        </div>

        <!-- TAB 4: FACT-CHECK TOOLKIT / 5 STEPS -->
        <div id="tab-toolkit" class="hidden space-y-6">
            <div class="p-6 sm:p-8 rounded-3xl neumorphism-card bg-white space-y-6">
                <div>
                    <h2 class="text-xl sm:text-2xl font-extrabold mb-2">Cẩm Nang 5 Bước Kiểm Chứng Nguồn Tin</h2>
                    <p class="text-slate-600 dark:text-slate-400 text-xs sm:text-sm">
                        Trang bị kỹ năng cốt lõi giúp bạn tự bảo vệ bản thân trước làn sóng thông tin xuyên tạc trên Internet.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                    <div class="p-5 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-800 space-y-2">
                        <div class="w-8 h-8 rounded-xl bg-sky-100 dark:bg-sky-950 text-sky-600 dark:text-sky-400 font-bold flex items-center justify-center text-sm">1</div>
                        <h3 class="font-bold text-sm">Đừng chỉ đọc Tiêu đề (Headline)</h3>
                        <p class="text-xs text-slate-600 dark:text-slate-400 leading-relaxed">Nhiều trang tin dùng tiêu đề giật gân để câu view (clickbait) nhưng nội dung bên trong hoàn toàn không đúng sự thật.</p>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-800 space-y-2">
                        <div class="w-8 h-8 rounded-xl bg-indigo-100 dark:bg-indigo-950 text-indigo-600 dark:text-indigo-400 font-bold flex items-center justify-center text-sm">2</div>
                        <h3 class="font-bold text-sm">Kiểm tra Tác giả & Nguồn gốc</h3>
                        <p class="text-xs text-slate-600 dark:text-slate-400 leading-relaxed">Bài viết có được xuất bản bởi cơ quan báo chí chính thống uy tín không? Hay từ các blog cá nhân vô danh?</p>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-800 space-y-2">
                        <div class="w-8 h-8 rounded-xl bg-emerald-100 dark:bg-emerald-950 text-emerald-600 dark:text-emerald-400 font-bold flex items-center justify-center text-sm">3</div>
                        <h3 class="font-bold text-sm">Tìm kiếm Đảo Ngược Hình Ảnh</h3>
                        <p class="text-xs text-slate-600 dark:text-slate-400 leading-relaxed">Tin giả thường dùng ảnh cũ từ sự kiện khác hoặc ảnh cắt ghép AI. Hãy dùng Google Lens / Reverse Image Search.</p>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-800 space-y-2">
                        <div class="w-8 h-8 rounded-xl bg-amber-100 dark:bg-amber-950 text-amber-600 dark:text-amber-400 font-bold flex items-center justify-center text-sm">4</div>
                        <h3 class="font-bold text-sm">Kiểm tra Cảm Xúc Bản Thân</h3>
                        <p class="text-xs text-slate-600 dark:text-slate-400 leading-relaxed">Nếu bài viết khiến bạn tức giận tột độ hoặc hoảng sợ ngay lập tức, đó là dấu hiệu tin đang cố thao túng tâm lý bạn.</p>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-800 space-y-2">
                        <div class="w-8 h-8 rounded-xl bg-rose-100 dark:bg-rose-950 text-rose-600 dark:text-rose-400 font-bold flex items-center justify-center text-sm">5</div>
                        <h3 class="font-bold text-sm">Đối chiếu Báo chí Chính Thống</h3>
                        <p class="text-xs text-slate-600 dark:text-slate-400 leading-relaxed">Tra cứu xem các hãng thông tấn lớn (VTV, VnExpress, Tuổi Trẻ, Thanh Niên) có đưa tin về sự kiện này hay không.</p>
                    </div>

                    <div class="p-5 rounded-2xl bg-gradient-to-br from-sky-50 to-indigo-50 dark:from-sky-950/40 dark:to-indigo-950/40 border border-sky-200 dark:border-sky-900 flex flex-col justify-between">
                        <div>
                            <div class="text-xl mb-2">💡</div>
                            <h3 class="font-bold text-sky-900 dark:text-sky-300 text-sm">Quy tắc vàng</h3>
                            <p class="text-xs text-sky-700 dark:text-sky-400 mt-1 leading-relaxed">"Nghi ngờ trước khi chia sẻ". Đừng tiếp tay cho tin giả lan rộng!</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </main>

    <!-- Footer -->
    <footer class="w-full border-t border-slate-200 dark:border-slate-800 py-4 text-center text-xs text-slate-500 bg-white dark:bg-slate-900">
        Fact-Check Radar Pro &copy; 2026. Công cụ hỗ trợ nhận diện và phòng chống tin giả trên không gian mạng.
    </footer>

    <!-- Tooltip Modal / Floating Box for Highlighted Words -->
    <div id="wordTooltip" class="hidden fixed bottom-6 right-6 max-w-sm bg-slate-900 text-slate-100 p-4 rounded-2xl shadow-2xl border border-slate-700 z-50 animate-fade-in space-y-2">
        <div class="flex items-center justify-between">
            <span id="tooltipWord" class="font-bold text-sky-400 text-sm">Từ khóa</span>
            <button onclick="closeTooltip()" class="text-slate-400 hover:text-white text-xs px-2 py-0.5 rounded bg-slate-800">✕ Đóng</button>
        </div>
        <p id="tooltipDesc" class="text-xs text-slate-300 leading-relaxed">Giải thích lý do từ này bị nghi ngờ...</p>
    </div>

    <script>
        // --- AUDIO FEEDBACK WITH TONE.JS ---
        let soundEnabled = true;
        const synth = new Tone.Synth().toDestination();

        function playSound(type) {
            if (!soundEnabled) return;
            try {
                Tone.start();
                if (type === 'click') {
                    synth.triggerAttackRelease("C5", "32n");
                } else if (type === 'scan') {
                    synth.triggerAttackRelease("G4", "16n");
                    setTimeout(() => synth.triggerAttackRelease("E5", "16n"), 100);
                } else if (type === 'correct') {
                    synth.triggerAttackRelease("C5", "16n");
                    setTimeout(() => synth.triggerAttackRelease("G5", "8n"), 100);
                } else if (type === 'wrong') {
                    synth.triggerAttackRelease("E3", "8n");
                    setTimeout(() => synth.triggerAttackRelease("C3", "4n"), 150);
                }
            } catch (e) {
                console.log("Audio context note loaded", e);
            }
        }

        function toggleSound() {
            soundEnabled = !soundEnabled;
            document.getElementById('soundStatus').innerText = soundEnabled ? 'Bật' : 'Tắt';
            playSound('click');
        }

        // --- DARK MODE TOGGLE ---
        function toggleDarkMode() {
            const html = document.documentElement;
            if (html.classList.contains('dark')) {
                html.classList.remove('dark');
            } else {
                html.classList.add('dark');
            }
            playSound('click');
        }

        // --- TAB NAVIGATION ---
        function switchTab(tabId) {
            playSound('click');
            ['scanner', 'library', 'game', 'toolkit'].forEach(t => {
                document.getElementById(`tab-${t}`).classList.add('hidden');
                const btn = document.getElementById(`nav-${t}`);
                btn.className = "px-3.5 py-1.5 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition";
            });

            document.getElementById(`tab-${tabId}`).classList.remove('hidden');
            const activeBtn = document.getElementById(`nav-${tabId}`);
            activeBtn.className = "px-3.5 py-1.5 rounded-xl text-xs font-semibold bg-sky-500 text-white shadow-sm transition";
        }

        // --- RED FLAGS DICTIONARY ---
        const redFlagsMap = {
            "chấn động": { reason: "Từ ngữ giật gân (Clickbait), kích thích sự tò mò quá mức và ép người đọc bấm vào liên kết." },
            "bí mật động trời": { reason: "Cụm từ ám chỉ thuyết âm mưu, tạo cảm giác nắm giữ thông tin bị che giấu độc quyền." },
            "thần dược": { reason: "Từ phóng đại xuất hiện trong tin giả y tế, quảng cáo thực phẩm chức năng lừa đảo chữa bách bệnh." },
            "chữa dứt điểm": { reason: "Cam kết tuyệt đối không có căn cứ y khoa đáng tin cậy." },
            "chia sẻ ngay lập tức": { reason: "Kêu gọi hành động khẩn cấp (Urgency trap), ngăn cản nạn nhân suy nghĩ logic trước khi chia sẻ." },
            "không được bộ y tế công nhận": { reason: "Dấu hiệu cảnh báo sản phẩm chui, lậu, không rõ nguồn gốc." },
            "bí mật bị che giấu": { reason: "Kích động tâm lý nghi ngờ các cơ quan quản lý nhà nước hoặc chuyên môn." },
            "lợi nhuận 500%": { reason: "Bẫy lừa đảo tài chính, tiền ảo đa cấp với lợi nhuận phi lý." },
            "chắc chắn 100%": { reason: "Sự khẳng định tuyệt đối hiếm khi tồn tại trong tin tức chính thống." },
            "sự thật ngỡ ngàng": { reason: "Tiêu đề mang tính chất thao túng cảm xúc, giật gân, câu view." }
        };

        // --- SAMPLE FAKE NEWS DATA ---
        const sampleFakeNews = [
            {
                title: "Thần dược chữa dứt điểm tiểu đường chỉ sau 3 ngày không cần uống thuốc",
                category: "Y tế & Sức khỏe giả mạo",
                text: "CHẤN ĐỘNG! Bí mật động trời về thần dược gia truyền giúp chữa dứt điểm tiểu đường 100% chỉ sau 3 ngày mà không cần dùng thuốc tây. Đây là bí mật bị che giấu bởi các tập đoàn dược phẩm lớn. HÃY CHIA SẺ NGAY LẬP TỨC trước khi bài viết bị xóa!"
            },
            {
                title: "Mẹo đầu tư tài chính bỏ ra 500k thu lãi 50 triệu mỗi tuần",
                category: "Lừa đảo tài chính / Đa cấp",
                text: "Cơ hội đổi đời có một không hai! Chỉ cần đầu tư 500.000đ vào ứng dụng công nghệ mới, chắc chắn 100% nhận lợi nhuận 500% sau 7 ngày. Sự thật ngỡ ngàng khi hàng nghìn người đã mua ô tô nhà lầu. Đăng ký ngay hôm nay!"
            },
            {
                title: "Phát hiện UFO hạ cánh tại khu vực vùng cao phía Bắc",
                category: "Tin đồn hoang đường / Thuyết âm mưu",
                text: "Chấn động mạng xã hội hình ảnh đĩa bay UFO xuất hiện ban đêm. Người dân hoang mang vì chính quyền giữ kín thông tin. Hãy chia sẻ ngay lập tức để người thân cảnh giác!"
            },
            {
                title: "Nước chanh nóng đun sôi diệt sạch tế bào ung thư lập tức",
                category: "Y tế phản khoa học",
                text: "Bác sĩ đầu ngành tiết lộ bí mật động trời: Uống nước chanh nóng lúc đói buổi sáng có khả năng chữa dứt điểm ung thư mạnh gấp 10.000 lần hóa trị mà Bộ Y tế không muốn bạn biết."
            }
        ];

        window.onload = function() {
            const container = document.getElementById('fakeNewsCardsContainer');
            container.innerHTML = '';

            sampleFakeNews.forEach((item, index) => {
                const card = document.createElement('div');
                card.className = 'p-5 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-800 flex flex-col justify-between space-y-3';
                card.innerHTML = `
                    <div>
                        <span class="text-[10px] font-semibold uppercase px-2.5 py-1 rounded-full bg-rose-50 dark:bg-rose-950 text-rose-600 dark:text-rose-400 border border-rose-100 dark:border-rose-900">${item.category}</span>
                        <h3 class="font-bold text-sm sm:text-base mt-2">${item.title}</h3>
                        <p class="text-xs text-slate-600 dark:text-slate-400 mt-1 line-clamp-3 leading-relaxed">"${item.text}"</p>
                    </div>
                    <button onclick="loadIntoScanner(${index})" class="w-full py-2 rounded-xl bg-sky-50 dark:bg-sky-950/40 border border-sky-200 dark:border-sky-900 text-xs font-semibold text-sky-700 dark:text-sky-300 hover:bg-sky-100 dark:hover:bg-sky-900 transition">
                        🔍 Thử nghiệm ngay vào bộ quét
                    </button>
                `;
                container.appendChild(card);
            });
        };

        function loadSampleText() {
            const samples = sampleFakeNews.map(s => s.text);
            const randomText = samples[Math.floor(Math.random() * samples.length)];
            document.getElementById('textInput').value = randomText;
            switchTab('scanner');
            analyzeText();
        }

        function loadIntoScanner(index) {
            document.getElementById('textInput').value = sampleFakeNews[index].text;
            switchTab('scanner');
            analyzeText();
        }

        function clearScanner() {
            document.getElementById('textInput').value = '';
            document.getElementById('resultBox').classList.add('hidden');
            document.getElementById('riskScoreNum').innerText = '0%';
            document.getElementById('riskScoreCircle').style.borderColor = '#e2e8f0';
            document.getElementById('riskLevelText').innerText = 'Chưa có dữ liệu phân tích';
            document.getElementById('redFlagsList').innerHTML = '<div class="p-3 rounded-xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-xs text-slate-500 text-center">Chưa phát hiện từ khóa khả nghi nào.</div>';
        }

        function copyReport() {
            const outputText = document.getElementById('highlightedOutput').innerText;
            navigator.clipboard.writeText(outputText);
            alert("Đã sao chép nội dung báo cáo kết quả quét!");
        }

        // --- SCANNER ANALYSIS LOGIC ---
        function analyzeText() {
            playSound('scan');
            const text = document.getElementById('textInput').value.trim();
            if (!text) {
                alert("Vui lòng nhập hoặc dán văn bản cần quét!");
                return;
            }

            let highlightedHtml = text;
            let foundFlags = [];
            let riskPoints = 0;

            Object.keys(redFlagsMap).forEach(keyword => {
                const regex = new RegExp(`(${keyword})`, 'gi');
                if (regex.test(text)) {
                    riskPoints += 25;
                    foundFlags.push({ keyword: keyword, reason: redFlagsMap[keyword].reason });
                    highlightedHtml = highlightedHtml.replace(regex, `<span class="highlight-redflag" onclick="showTooltip('${keyword}')">$1</span>`);
                }
            });

            let riskScore = Math.min(riskPoints, 100);
            if (riskScore === 0 && text.length > 20) riskScore = 10;

            document.getElementById('resultBox').classList.remove('hidden');
            document.getElementById('highlightedOutput').innerHTML = highlightedHtml;

            document.getElementById('riskScoreNum').innerText = riskScore + '%';
            const circle = document.getElementById('riskScoreCircle');
            const levelText = document.getElementById('riskLevelText');

            if (riskScore >= 70) {
                circle.style.borderColor = '#ef4444';
                levelText.innerHTML = '<span class="text-rose-600">🚨 NGUY CƠ TIN GIẢ RẤT CAO!</span>';
            } else if (riskScore >= 30) {
                circle.style.borderColor = '#f59e0b';
                levelText.innerHTML = '<span class="text-amber-600">⚠️ CÓ DẤU HIỆU KHẢ NGHI / GIẬT GÂN</span>';
            } else {
                circle.style.borderColor = '#10b981';
                levelText.innerHTML = '<span class="text-emerald-600">✅ THÔNG TIN TƯƠNG ĐỐI AN TOÀN</span>';
            }

            const listContainer = document.getElementById('redFlagsList');
            listContainer.innerHTML = '';

            if (foundFlags.length === 0) {
                listContainer.innerHTML = '<div class="p-3 rounded-xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-xs text-slate-500 text-center">Không tìm thấy từ khóa giật gân đặc thù nào.</div>';
            } else {
                foundFlags.forEach(flag => {
                    const div = document.createElement('div');
                    div.className = 'p-3 rounded-xl bg-rose-50 dark:bg-rose-950/50 border border-rose-100 dark:border-rose-900 text-xs space-y-1';
                    div.innerHTML = `
                        <div class="font-bold text-rose-700 dark:text-rose-400">🔹 "${flag.keyword}"</div>
                        <div class="text-slate-600 dark:text-slate-300 leading-relaxed">${flag.reason}</div>
                    `;
                    listContainer.appendChild(div);
                });
            }
        }

        function showTooltip(keyword) {
            playSound('click');
            const info = redFlagsMap[keyword];
            if (info) {
                document.getElementById('tooltipWord').innerText = `Từ khóa: "${keyword}"`;
                document.getElementById('tooltipDesc').innerText = info.reason;
                document.getElementById('wordTooltip').classList.remove('hidden');
            }
        }

        function closeTooltip() {
            document.getElementById('wordTooltip').classList.add('hidden');
        }

        // --- FACT-CHECK GAME DATA & LOGIC ---
        const gameQuestions = [
            {
                question: "Bạn thấy một bài viết trên Facebook chia sẻ ảnh đám mây hình nấm kèm thông tin 'Bom nguyên tử vừa phát nổ tại nhà máy điện hạt nhân gần biên giới'. Bạn nên làm gì đầu tiên?",
                options: [
                    "Hoảng sợ và chia sẻ ngay lên nhóm gia đình để mọi người tránh.",
                    "Kiểm tra xem các hãng thông tấn chính thống (VTV, VnExpress) có đưa tin không và tìm kiếm ngược hình ảnh đám mây.",
                    "Tin ngay vì hình ảnh rất chân thực không thể chỉnh sửa."
                ],
                correct: 1,
                explanation: "Tin giả thường dùng ảnh cũ hoặc ảnh ghép để tạo hoảng loạn. Luôn đối chiếu báo chính thống trước khi chia sẻ."
            },
            {
                question: "Một trang web đăng bài 'Bí quyết giảm 15kg mỡ bụng trong 2 tuần chỉ bằng việc ngửi tinh dầu lạ'. Đây là dấu hiệu gì?",
                options: [
                    "Tin khoa học đột phá mới được phát hiện.",
                    "Chiêu trò quảng cáo lừa đảo, phóng đại công dụng (Clickbait / Fake product).",
                    "Thông tin dinh dưỡng chuẩn từ bác sĩ."
                ],
                correct: 1,
                explanation: "Giảm cân khoa học cần thời gian và chế độ dinh dưỡng, không thể giảm số lượng lớn cấp tốc bằng các phương pháp phản khoa học."
            },
            {
                question: "Khi đọc một tiêu đề bài báo kích động sự phẫn nộ tột độ đối với một cá nhân, phản ứng tư duy phản biện đúng đắn là gì?",
                options: [
                    "Vào bình luận chửi mắng ngay lập tức để bày tỏ chính nghĩa.",
                    "Tạm dừng lại, đặt câu hỏi về động cơ của tác giả và tìm đọc toàn bộ bài viết thay vì chỉ đọc tiêu đề giật gân.",
                    "Chuyển tiếp bài viết cho tất cả bạn bè."
                ],
                correct: 1,
                explanation: "Tiêu đề giật gân nhằm câu view và kích động cảm xúc giận dữ. Hãy giữ cái đầu lạnh và đọc toàn bộ nội dung."
            },
            {
                question: "Làm thế nào để nhận biết một hình ảnh trên mạng xã hội có phải là ảnh cắt ghép AI hoặc ảnh giả mạo sự kiện cũ không?",
                options: [
                    "Sử dụng công cụ tìm kiếm hình ảnh ngược (Google Reverse Image Search / Google Lens).",
                    "Nhìn bằng mắt thường là chắc chắn phân biệt được 100%.",
                    "Không có cách nào kiểm tra ngoài đời thực."
                ],
                correct: 0,
                explanation: "Công cụ tìm kiếm ngược hình ảnh giúp bạn biết bức ảnh đó thực chất xuất hiện từ năm nào và ở sự kiện nào."
            }
        ];

        let gameIndex = 0;
        let gameScoreCount = 0;

        function startGame() {
            playSound('click');
            gameIndex = 0;
            gameScoreCount = 0;
            document.getElementById('gameStartContainer').classList.add('hidden');
            document.getElementById('gameResultContainer').classList.add('hidden');
            document.getElementById('gamePlayContainer').classList.remove('hidden');
            loadGameQuestion();
        }

        function loadGameQuestion() {
            const q = gameQuestions[gameIndex];
            document.getElementById('gameCurrQ').innerText = gameIndex + 1;
            document.getElementById('gameScore').innerText = gameScoreCount;
            document.getElementById('gameQuestionText').innerText = q.question;
            document.getElementById('gameExplanationBox').classList.add('hidden');

            const optionsContainer = document.getElementById('gameOptionsList');
            optionsContainer.innerHTML = '';

            q.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.className = 'p-4 rounded-2xl bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-800 text-left text-xs sm:text-sm text-slate-700 dark:text-slate-300 hover:border-sky-400 hover:bg-sky-50 dark:hover:bg-slate-800 transition flex items-center gap-3 font-medium';
                btn.innerHTML = `
                    <span class="w-6 h-6 rounded-lg bg-slate-200 dark:bg-slate-800 flex items-center justify-center font-mono text-xs">${String.fromCharCode(65 + idx)}</span>
                    <span class="flex-1">${opt}</span>
                `;
                btn.onclick = () => selectGameAnswer(idx);
                optionsContainer.appendChild(btn);
            });
        }

        function selectGameAnswer(selectedIndex) {
            const q = gameQuestions[gameIndex];
            const isCorrect = selectedIndex === q.correct;
            const buttons = document.getElementById('gameOptionsList').children;

            for (let i = 0; i < buttons.length; i++) {
                buttons[i].disabled = true;
                if (i === q.correct) {
                    buttons[i].classList.add('bg-emerald-50', 'dark:bg-emerald-950/50', 'border-emerald-500', 'text-emerald-900', 'dark:text-emerald-300');
                } else if (i === selectedIndex && !isCorrect) {
                    buttons[i].classList.add('bg-rose-50', 'dark:bg-rose-950/50', 'border-rose-500', 'text-rose-900', 'dark:text-rose-300');
                }
            }

            if (isCorrect) {
                playSound('correct');
                gameScoreCount += 25;
            } else {
                playSound('wrong');
            }

            document.getElementById('gameExpTitle').innerText = isCorrect ? "✅ Chính xác tuyệt vời!" : "❌ Chưa chính xác!";
            document.getElementById('gameExpText').innerText = q.explanation;
            document.getElementById('gameExplanationBox').classList.remove('hidden');
        }

        function nextGameQuestion() {
            playSound('click');
            gameIndex++;
            if (gameIndex < gameQuestions.length) {
                loadGameQuestion();
            } else {
                showGameResult();
            }
        }

        function showGameResult() {
            playSound('correct');
            confetti({ particleCount: 120, spread: 70, origin: { y: 0.6 } });

            document.getElementById('gamePlayContainer').classList.add('hidden');
            document.getElementById('gameResultContainer').classList.remove('hidden');
            document.getElementById('gameFinalSummary').innerText = `Bạn đã hoàn thành thử thách với số điểm: ${gameScoreCount}/100 điểm. Tư duy phản biện của bạn rất xuất sắc!`;
        }

        function resetGame() {
            startGame();
        }
    </script>
</body>
</html>
