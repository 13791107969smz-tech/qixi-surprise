<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>七夕惊喜 - 给方子颜</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background-color: #080810;
            color: #ffffff;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
            overflow: hidden;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        #fireworksCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }
        .container {
            position: relative;
            z-index: 2;
            width: 90%;
            max-width: 500px;
            text-align: center;
        }
        .scene {
            display: none;
            opacity: 0;
            transition: opacity 1s ease-in-out;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 20px;
            padding: 30px 20px;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
        }
        .scene.active {
            display: block;
            opacity: 1;
        }
        .time-badge {
            font-size: 0.9rem;
            color: #aaa;
            margin-bottom: 15px;
            letter-spacing: 2px;
        }
        .phone-notice {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 15px;
            margin: 20px 0;
            text-align: left;
            border-left: 4px solid #ff4b5c;
        }
        .phone-title {
            font-size: 0.85rem;
            color: #ff85a2;
            margin-bottom: 5px;
        }
        .phone-body {
            font-size: 1.05rem;
        }
        .btn {
            background: linear-gradient(135deg, #ff4b5c, #ff758c);
            color: white;
            border: none;
            padding: 12px 28px;
            font-size: 1rem;
            border-radius: 25px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(255, 75, 92, 0.4);
            transition: transform 0.2s, box-shadow 0.2s;
            margin-top: 15px;
        }
        .btn:hover {
            transform: scale(1.03);
            box-shadow: 0 6px 20px rgba(255, 75, 92, 0.6);
        }
        .story-text {
            line-height: 1.8;
            font-size: 1.05rem;
            color: #e0e0e0;
            text-align: left;
            margin-bottom: 20px;
        }
        .card {
            background: rgba(255, 240, 243, 0.95);
            color: #333;
            border-radius: 12px;
            padding: 25px;
            text-align: left;
            line-height: 1.8;
            margin: 15px 0;
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
            font-size: 0.98rem;
        }
        .card-title {
            color: #d63384;
            font-weight: bold;
            font-size: 1.1rem;
            margin-bottom: 10px;
        }
        .final-wish {
            font-size: 1.8rem;
            font-weight: bold;
            color: #ff4b5c;
            text-shadow: 0 0 10px rgba(255, 75, 92, 0.8);
            margin-top: 15px;
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>

    <canvas id="fireworksCanvas"></canvas>

    <div class="container">
        <!-- 场景 1：深夜与消息 -->
        <div class="scene active" id="scene1">
            <div class="time-badge">2026 年 七夕零点 00:00</div>
            <p style="color: #bbb; font-size: 0.95rem;">深夜，四周一片安静。</p>
            <div class="phone-notice">
                <div class="phone-title">💬 收到一条新消息</div>
                <div class="phone-body">“睡了吗？看看窗外。”</div>
            </div>
            <p style="font-size: 0.9rem; color: #aaa; margin-top: 10px;">突然，窗外隐约传来了烟花升空绽放的声音……</p>
            <button class="btn" onclick="goToScene(2)">拉开窗帘 ✨</button>
        </div>

        <!-- 场景 2：窗外烟花与走来的男孩 -->
        <div class="scene" id="scene2">
            <div class="story-text">
                你推开窗户，漆黑的夜空瞬间被漫天绚丽的烟花照亮。<br><br>
                在漫天星光与璀璨的花火下，你看到那个熟悉的身影，正抱着一束精心准备的花，微笑着缓缓向你走来……
            </div>
            <button class="btn" onclick="goToScene(3)">接过花束并打开卡片 🌹</button>
        </div>

        <!-- 场景 3：花中的卡片内容 -->
        <div class="scene" id="scene3">
            <div class="card">
                <div class="card-title">致 方子颜：</div>
                在这个平静而又特殊的夜晚，我想把所有的星光与温柔都送给你。<br><br>
                谢谢你走进我的世界，让每一个平凡的日子都变得闪闪发光。未来的每一个四季，我都想陪你一起看遍所有的烟火。
            </div>
            <button class="btn" onclick="goToScene(4)">看 向 他 💖</button>
        </div>

        <!-- 场景 4：最终祝福 -->
        <div class="scene" id="scene4">
            <div style="font-size: 3rem; margin-bottom: 10px;">🎆</div>
            <div class="final-wish">祝方子颜七夕快乐！</div>
            <p style="margin-top: 15px; color: #ddd; font-size: 0.95rem;">余生漫漫，爱意永不落幕。</p>
        </div>
    </div>

    <script>
        // 场景切换逻辑
        function goToScene(sceneNumber) {
            document.querySelectorAll('.scene').forEach(el => el.classList.remove('active'));
            const nextScene = document.getElementById(`scene${sceneNumber}`);
            if (nextScene) {
                nextScene.classList.add('active');
            }
            if (sceneNumber >= 2) {
                startFireworks();
            }
            if (sceneNumber === 4) {
                frequentFireworks();
            }
        }

        // 烟花画布效果
        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');
        let width = canvas.width = window.innerWidth;
        let height = canvas.height = window.innerHeight;

        window.addEventListener('resize', () => {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        });

        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                const angle = Math.random() * Math.PI * 2;
                const speed = Math.random() * 6 + 1;
                this.vx = Math.cos(angle) * speed;
                this.vy = Math.sin(angle) * speed;
                this.alpha = 1;
                this.decay = Math.random() * 0.015 + 0.008;
            }
            update() {
                this.x += this.vx;
                this.y += this.vy;
                this.vy += 0.05; // 重力
                this.alpha -= this.decay;
            }
            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2.5, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.restore();
            }
        }

        let particles = [];
        let fireworkInterval = null;

        function createExplosion(x, y) {
            const colors = ['#ff4b5c', '#ff758c', '#ffea00', '#00f5d4', '#7b2cbf', '#ffffff'];
            const color = colors[Math.floor(Math.random() * colors.length)];
            for (let i = 0; i < 50; i++) {
                particles.push(new Particle(x, y, color));
            }
        }

        function startFireworks() {
            if (fireworkInterval) return;
            fireworkInterval = setInterval(() => {
                createExplosion(
                    Math.random() * (width - 200) + 100,
                    Math.random() * (height * 0.5) + 50
                );
            }, 800);
        }

        function frequentFireworks() {
            if (fireworkInterval) clearInterval(fireworkInterval);
            fireworkInterval = setInterval(() => {
                createExplosion(
                    Math.random() * width,
                    Math.random() * (height * 0.6)
                );
            }, 300);
        }

        function animate() {
            ctx.fillStyle = 'rgba(8, 8, 16, 0.2)';
            ctx.fillRect(0, 0, width, height);

            for (let i = particles.length - 1; i >= 0; i--) {
                particles[i].update();
                particles[i].draw();
                if (particles[i].alpha <= 0) {
                    particles.splice(i, 1);
                }
            }
            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>

