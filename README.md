<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2024龙年大吉</title>
    <style>
        /* 移动端适配 */
        body { margin: 0; overflow: hidden; background: #000; }
        #app { position: relative; height: 100vh; }
        
        /* 烟花画布 */
        #firework-canvas { 
            position: absolute;
            width: 100%;
            height: 60vh;
        }

        /* 微信风格按钮 */
        .weui-btn {
            background: #e64340;
            color: white;
            border-radius: 25px;
            padding: 12px 0;
            margin: 15px 20%;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div id="app">
        <canvas id="firework-canvas"></canvas>
        <button class="weui-btn" onclick="showBlessing()">🎉 生成我的祝福</button>
        <button class="weui-btn" onclick="showZodiac()">🔮 生肖运势占卜</button>
    </div>

    <!-- 微信分享SDK -->
    <script src="https://res.wx.qq.com/open/js/jweixin-1.6.0.js"></script>
    
    <script>
// ================= 烟花动画系统 =================
class FireworkSystem {
    constructor(canvas) {
        this.canvas = canvas;
        this.ctx = canvas.getContext('2d');
        this.particles = [];
        
        // 自适应画布大小
        window.addEventListener('resize', () => this.resizeCanvas());
        this.resizeCanvas();
    }

    resizeCanvas() {
        this.canvas.width = window.innerWidth;
        this.canvas.height = window.innerHeight * 0.6;
    }

    launch() {
        // 烟花粒子生成逻辑
        const createParticle = (x, y) => ({
