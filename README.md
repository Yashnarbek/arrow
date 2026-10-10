<!-- Header / Nav -->
<header class="bg-slate-900/90 backdrop-blur-md border-b border-slate-800 py-3 px-4 z-20 shrink-0">
    <div class="max-w-6xl mx-auto flex justify-between items-center">
        <div class="flex items-center space-x-3">
            <div class="bg-gradient-to-tr from-purple-400 to-indigo-600 text-white p-2 rounded-xl shadow-md shadow-purple-500/20 text-base font-black">
                🛸
            </div>
            <div>
                <h1 class="text-sm md:text-base font-black bg-gradient-to-r from-purple-400 to-indigo-400 bg-clip-text text-transparent">Sky Math: Professional Doska</h1>
            </div>
        </div>
        <div id="game-stats" class="hidden flex items-center space-x-3 bg-slate-950/80 px-3 py-1.5 rounded-xl border border-slate-800 text-xs md:text-sm">
            <div>Balandlik: <span id="stat-altitude" class="font-bold text-purple-400">80%</span></div>
            <div class="text-slate-700">|</div>
            <div>Ball: <span id="stat-score" class="font-bold text-emerald-400">0</span></div>
            <div class="text-slate-700">|</div>
            <div>Bosqich: <span id="stat-level" class="font-bold text-amber-400">1</span></div>
            <div class="text-slate-700">|</div>
            <button onclick="startGame()" class="bg-rose-950/60 hover:bg-rose-900/80 text-rose-300 border border-rose-900/50 px-2 py-0.5 rounded-lg text-xs font-semibold transition-all" title="Qaytadan boshlash">🔄 Qayta</button>
        </div>
    </div>
</header>

<!-- Main Content Container -->
<main class="flex-grow flex flex-col items-center justify-center p-3 max-w-6xl mx-auto w-full my-auto">
    
    <!-- START SCREEN -->
    <div id="screen-start" class="w-full max-w-xl bg-slate-900/90 border border-slate-800 rounded-3xl p-6 md:p-10 shadow-2xl text-center space-y-6 backdrop-blur-xl">
        <div class="inline-flex p-4 bg-purple-500/10 rounded-full text-purple-400 border border-purple-500/20 animate-bounce">
            <svg class="w-12 h-12" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-2h2v2zm0-4h-2V7h2v6z"></path></svg>
        </div>
        <div class="space-y-2">
            <h2 class="text-2xl md:text-3xl font-black tracking-tight text-white">Ikki Ustunli Uchar Tarelka Doskasi</h2>
            <p class="text-slate-300 text-xs md:text-sm leading-relaxed max-w-lg mx-auto">
                Chap tomonda <span class="text-purple-400 font-semibold">Kalkulyator</span> bloki, o'ng tomonda esa uchar tarelka parvozi va kengaytirilgan topshiriqlar ekrani! <span class="text-emerald-400 font-semibold">Vaqt cheklovi yo'q</span>, xotirjam hisoblang va ball yig'ing.
            </p>
        </div>

        <!-- Difficulty Selection -->
        <div class="max-w-xs mx-auto grid grid-cols-3 gap-2">
            <button onclick="setDifficulty('easy')" id="diff-easy" class="diff-btn py-2.5 px-2 rounded-xl font-bold text-xs border border-purple-500 bg-purple-600 text-white shadow-md shadow-purple-500/20 transition-all">Oson</button>
            <button onclick="setDifficulty('medium')" id="diff-medium" class="diff-btn py-2.5 px-2 rounded-xl font-bold text-xs border border-slate-800 bg-slate-950 text-slate-400 hover:border-slate-700 transition-all">O'rta</button>
            <button onclick="setDifficulty('hard')" id="diff-hard" class="diff-btn py-2.5 px-2 rounded-xl font-bold text-xs border border-slate-800 bg-slate-950 text-slate-400 hover:border-slate-700 transition-all">Qiyin</button>
        </div>

        <div class="pt-2">
            <button onclick="startGame()" class="w-full max-w-xs bg-gradient-to-r from-purple-500 to-indigo-600 hover:from-purple-600 hover:to-indigo-700 text-white font-black py-3 px-6 rounded-2xl shadow-lg shadow-purple-500/30 transition-all transform active:scale-95 text-sm">
                Parvozni Boshlash 🛸
            </button>
        </div>
    </div>

    <!-- GAMEPLAY SCREEN: TWO COLUMNS (Keypad Left, Screen Right) -->
    <div id="screen-game" class="hidden w-full grid grid-cols-1 md:grid-cols-12 gap-5 items-start">
        
        <!-- LEFT COLUMN: Keypad & Input Box -->
        <div class="md:col-span-4 bg-slate-900/95 border border-slate-800 rounded-2xl p-5 shadow-xl space-y-4 backdrop-blur-xl">
            <div class="flex justify-between items-center border-b border-slate-800 pb-2">
                <span class="text-xs font-black text-slate-400 uppercase tracking-wider">Hisoblash Paneli</span>
                <div class="flex items-center space-x-2">
                    <span class="text-[10px] text-slate-500 font-bold uppercase">Javob:</span>
                    <div id="answer-input-display" class="text-xl font-black text-purple-400 tracking-wider min-w-[70px] text-right bg-slate-950 px-2 py-0.5 rounded border border-slate-800">_</div>
                </div>
            </div>

            <!-- Calculator Keypad Grid -->
            <div class="grid grid-cols-3 gap-2.5 pt-1">
                <button onclick="appendNum('1')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">1</button>
                <button onclick="appendNum('2')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">2</button>
                <button onclick="appendNum('3')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">3</button>
                
                <button onclick="appendNum('4')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">4</button>
                <button onclick="appendNum('5')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">5</button>
                <button onclick="appendNum('6')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">6</button>
                
                <button onclick="appendNum('7')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">7</button>
                <button onclick="appendNum('8')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">8</button>
                <button onclick="appendNum('9')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-4 rounded-xl text-base transition-all active:scale-95 shadow">9</button>
                
                <button onclick="clearInput()" class="bg-rose-950/40 hover:bg-rose-900/50 border border-rose-900/50 text-rose-300 font-bold py-3.5 rounded-xl text-sm transition-all active:scale-95">C</button>
                <button onclick="appendNum('0')" class="bg-slate-950 hover:bg-slate-800 border border-slate-800 text-slate-200 font-bold py-3.5 rounded-xl text-base transition-all active:scale-95 shadow">0</button>
                <button onclick="submitAnswer()" class="bg-emerald-600 hover:bg-emerald-700 border border-emerald-500 text-white font-bold py-3.5 rounded-xl text-sm shadow-md shadow-emerald-600/30 transition-all active:scale-95">OK</button>
            </div>
        </div>

        <!-- RIGHT COLUMN: Real UFO Canvas & Question Display -->
        <div class="md:col-span-8 flex flex-col space-y-4">
            
            <!-- Canvas Display for Real UFO Simulator (Kattalashtirilgan ekran) -->
            <div class="relative w-full h-64 md:h-80 rounded-2xl overflow-hidden border border-slate-800 shadow-2xl bg-slate-950">
                <canvas id="gameCanvas" class="w-full h-full block"></canvas>
                <!-- Floating Alert on Canvas -->
                <div id="canvas-alert" class="absolute top-3 left-3 bg-slate-900/90 backdrop-blur-md px-3 py-1 rounded-lg border border-slate-700 text-xs font-semibold text-purple-300 transition-opacity opacity-0 z-10 shadow-lg">
                    + Balandlik ko'tarildi! 🛸
                </div>
            </div>

            <!-- Question Panel -->
            <div class="bg-slate-900/95 border border-slate-800 rounded-2xl p-5 shadow-xl space-y-3 backdrop-blur-xl">
                <div class="flex justify-between items-center">
                    <span id="question-badge" class="px-3.5 py-1 rounded-full text-xs font-black uppercase tracking-wider bg-purple-500/10 text-purple-400 border border-purple-500/20">
                        EKUB Topish
                    </span>
                    <span class="text-[11px] text-emerald-400 font-semibold bg-emerald-950/50 px-2.5 py-1 rounded border border-emerald-900/40">
                        Vaqt Cheklovisiz ♾️
                    </span>
                </div>

                <div class="flex items-center justify-between bg-slate-950/80 px-5 py-3 rounded-xl border border-slate-800">
                    <div class="text-2xl md:text-3xl font-black text-white tracking-wide" id="question-text">
                        24 va 36
                    </div>
                    <div class="text-xs md:text-sm text-slate-400 font-medium">
                        To'g'ri javoblar: <span id="correct-streak" class="font-bold text-purple-400">0</span>
                    </div>
                </div>
            </div>

        </div>
    </div>

    <!-- GAMEOVER SCREEN -->
    <div id="screen-gameover" class="hidden w-full max-w-md bg-slate-900/90 border border-slate-800 rounded-3xl p-6 md:p-8 shadow-2xl text-center space-y-6 backdrop-blur-xl">
        <div class="inline-flex p-4 bg-rose-500/10 rounded-full text-rose-400 border border-rose-500/20">
            <svg class="w-14 h-14" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"></path></svg>
        </div>
        <div class="space-y-1">
            <h2 class="text-2xl md:text-3xl font-black text-white">Uchar Tarelka Yerga Quladi!</h2>
            <p class="text-slate-400 text-xs md:text-sm">Ajoyib urinish! Sizning yakuniy natijangiz:</p>
        </div>

        <div class="bg-slate-950/60 border border-slate-800 p-4 rounded-2xl max-w-xs mx-auto space-y-3">
            <div>
                <span class="text-xs text-slate-400 uppercase tracking-wider block font-semibold">To'plangan Ball</span>
                <span id="final-score" class="text-3xl font-black text-emerald-400">0</span>
            </div>
            <div class="border-t border-slate-900 pt-2 flex justify-around text-xs md:text-sm">
                <div>
                    <span class="text-[10px] text-slate-400 block">To'g'ri Javoblar</span>
                    <span id="final-correct" class="font-bold text-purple-400">0</span>
                </div>
                <div>
                    <span class="text-[10px] text-slate-400 block">Bosqich</span>
                    <span id="final-level" class="font-bold text-amber-400">1</span>
                </div>
            </div>
        </div>

        <div class="flex gap-2 justify-center pt-1">
            <button onclick="startGame()" class="bg-gradient-to-r from-purple-500 to-indigo-600 hover:from-purple-600 hover:to-indigo-700 text-white font-bold py-3 px-5 rounded-xl shadow-md shadow-purple-500/25 transition-all text-xs md:text-sm">
                Qaytadan Uchish 🔄
            </button>
            <button onclick="showStartScreen()" class="bg-slate-800 hover:bg-slate-700 text-slate-300 font-semibold py-3 px-5 rounded-xl transition-all text-xs md:text-sm">
                Menyu 🏠
            </button>
        </div>
    </div>

</main>

<footer class="text-center py-2 text-[11px] text-slate-500 border-t border-slate-800/80 shrink-0">
    Sky Math &bull; Ikki Ustunli Kalkulyator va Real Uchar Tarelka Rejimi
</footer>

<script>
    let currentDifficulty = 'easy';
    let score = 0;
    let level = 1;
    let correctCount = 0;
    let altitude = 80;
    let descentRate = 0.04;
    let gameActive = false;
    
    let currentQuestion = null;
    let userAnswerStr = "";
    let animationFrameId = null;

    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    let stars = [
        { x: 50, y: 30, size: 2, alpha: 0.8 },
        { x: 150, y: 80, size: 1.5, alpha: 0.5 },
        { x: 280, y: 40, size: 2.5, alpha: 0.9 },
        { x: 400, y: 100, size: 1, alpha: 0.6 },
        { x: 520, y: 50, size: 2, alpha: 0.7 }
    ];

    let audioCtx = null;
    function getAudioContext() {
        if (!audioCtx) {
            audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        }
        if (audioCtx.state === 'suspended') {
            audioCtx.resume();
        }
        return audioCtx;
    }

    function playGoGoGoSound() {
        try {
            const ctxAudio = getAudioContext();
            let notes = [523.25, 659.25, 783.99, 1046.50];
            notes.forEach((freq, index) => {
                let osc = ctxAudio.createOscillator();
                let gain = ctxAudio.createGain();
                osc.type = 'triangle';
                osc.frequency.setValueAtTime(freq, ctxAudio.currentTime + index * 0.12);
                
                gain.gain.setValueAtTime(0.2, ctxAudio.currentTime + index * 0.12);
                gain.gain.exponentialRampToValueAtTime(0.001, ctxAudio.currentTime + index * 0.12 + 0.25);
                
                osc.connect(gain);
                gain.connect(ctxAudio.destination);
                
                osc.start(ctxAudio.currentTime + index * 0.12);
                osc.stop(ctxAudio.currentTime + index * 0.12 + 0.25);
            });
        } catch (e) {
            console.log("Audio not allowed yet");
        }
    }

    function playFunnyLaughSound() {
        try {
            const ctxAudio = getAudioContext();
            let times = [0, 0.1, 0.2, 0.3, 0.4, 0.5];
            let freqs = [350, 280, 400, 310, 440, 250];
            times.forEach((t, i) => {
                let osc = ctxAudio.createOscillator();
                let gain = ctxAudio.createGain();
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(freqs[i], ctxAudio.currentTime + t);
                
                gain.gain.setValueAtTime(0.15, ctxAudio.currentTime + t);
                gain.gain.exponentialRampToValueAtTime(0.001, ctxAudio.currentTime + t + 0.12);
                
                osc.connect(gain);
                gain.connect(ctxAudio.destination);
                
                osc.start(ctxAudio.currentTime + t);
                osc.stop(ctxAudio.currentTime + t + 0.12);
            });
        } catch (e) {
            console.log("Audio not allowed yet");
        }
    }

    function gcd(a, b) {
        while (b !== 0) {
            let temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }

    function lcm(a, b) {
        return (a * b) / gcd(a, b);
    }

    function setDifficulty(diff) {
        currentDifficulty = diff;
        document.querySelectorAll('.diff-btn').forEach(btn => {
            btn.className = "diff-btn py-2.5 px-2 rounded-xl font-bold text-xs border border-slate-800 bg-slate-950 text-slate-400 hover:border-slate-700 transition-all";
        });
        const activeBtn = document.getElementById(`diff-${diff}`);
        if (activeBtn) {
            activeBtn.className = "diff-btn py-2.5 px-2 rounded-xl font-bold text-xs border border-purple-500 bg-purple-600 text-white shadow-md shadow-purple-500/20 transition-all";
        }
    }

    function showScreen(screenId) {
        ['screen-start', 'screen-game', 'screen-gameover'].forEach(id => {
            const el = document.getElementById(id);
            if (el) el.classList.add('hidden');
        });
        const target = document.getElementById(screenId);
        if (target) target.classList.remove('hidden');

        const statsBadge = document.getElementById('game-stats');
        if (statsBadge) {
            if (screenId === 'screen-game') {
                statsBadge.classList.remove('hidden');
            } else {
                statsBadge.classList.add('hidden');
            }
        }
    }

    function showStartScreen() {
        gameActive = false;
        cancelAnimationFrame(animationFrameId);
        showScreen('screen-start');
    }

    function startGame() {
        score = 0;
        level = 1;
        correctCount = 0;
        altitude = 75;
        userAnswerStr = "";
        updateInputDisplay();
        
        if (currentDifficulty === 'easy') descentRate = 0.035;
        else if (currentDifficulty === 'medium') descentRate = 0.055;
        else descentRate = 0.08;

        gameActive = true;
        showScreen('screen-game');
        resizeCanvas();
        nextQuestion();
        loop();
    }

    function resizeCanvas() {
        if (canvas && canvas.parentElement) {
            canvas.width = canvas.parentElement.clientWidth;
            canvas.height = canvas.parentElement.clientHeight;
        }
    }

    window.addEventListener('resize', () => {
        if (gameActive) resizeCanvas();
    });

    function appendNum(num) {
        if (!game

Shu kodni   public qilib ber
