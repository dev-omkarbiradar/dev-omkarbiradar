<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Tech Stack Sphere</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: linear-gradient(135deg, #0d1117 0%, #161b22 50%, #21262d 100%);
            overflow: hidden;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        #container {
            width: 100vw;
            height: 100vh;
            position: relative;
            cursor: grab;
        }
        #container:active {
            cursor: grabbing;
        }
        #title {
            position: absolute;
            top: 30px;
            left: 50%;
            transform: translateX(-50%);
            color: #58a6ff;
            font-size: 2.5rem;
            font-weight: bold;
            text-align: center;
            z-index: 100;
            text-shadow: 0 0 20px rgba(88, 166, 255, 0.6);
            animation: titleGlow 2s ease-in-out infinite alternate;
        }
        @keyframes titleGlow {
            from { text-shadow: 0 0 20px rgba(88, 166, 255, 0.6); }
            to { text-shadow: 0 0 30px rgba(88, 166, 255, 0.9), 0 0 40px rgba(88, 166, 255, 0.4); }
        }
        #title .emoji {
            display: inline-block;
            animation: spin 3s linear infinite;
            margin-right: 10px;
        }
        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        .tech-info {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            color: #7d8590;
            text-align: center;
            z-index: 100;
            font-size: 14px;
        }
        .tech-categories {
            position: absolute;
            top: 100px;
            left: 20px;
            color: #f0f6fc;
            z-index: 100;
            background: rgba(13, 17, 23, 0.8);
            padding: 20px;
            border-radius: 10px;
            border: 1px solid #30363d;
            backdrop-filter: blur(10px);
        }
        .category {
            margin-bottom: 15px;
            font-size: 14px;
        } 
        .category-title {
            font-weight: bold;
            margin-bottom: 5px;
            color: #58a6ff;
        }
        .loading {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: #58a6ff;
            font-size: 18px;
            z-index: 200;
        }
        .controls {
            position: absolute;
            bottom: 30px;
            right: 30px;
            color: #7d8590;
            font-size: 12px;
            text-align: right;
            z-index: 100;
        }
    </style>
</head>
<body>
    <div id="container">
        <div id="title">
            <span class="emoji">⚙️</span>Tech Stack
        </div>
        <div class="loading" id="loading">Loading 3D Experience...</div>
        <div class="tech-categories">
            <div class="category">
                <div class="category-title">⚡ Languages</div>
                <div>JavaScript, Python, HTML5, CSS3</div>
            </div>
            <div class="category">
                <div class="category-title">🚀 Frameworks</div>
                <div>React, Node.js, Flask, FastAPI</div>
            </div>
            <div class="category">
                <div class="category-title">💾 Databases</div>
                <div>MongoDB, PostgreSQL, MySQL</div>
            </div>
            <div class="category">
                <div class="category-title">⚙️ DevOps</div>
                <div>Git, GitHub, Vercel, Vite</div>
            </div>
            <div class="category">
                <div class="category-title">🧠 AI & ML</div>
                <div>GitHub Copilot, Gemini, Hugging Face</div>
            </div>
        </div>
        <div class="tech-info">
            Interactive 3D visualization of my technology stack • Drag to rotate • Scroll to zoom
        </div>
        <div class="controls">
            🖱️ Drag to rotate<br>
            🔍 Scroll to zoom<br>
            ⚡ Auto-rotating sphere
        </div>
    </div>
    <script>
        // Tech stack data with colors and positions
        const techStack = [
            // Languages
            { name: 'JavaScript', color: 0xF7DF1E, category: 'language' },
            { name: 'Python', color: 0x3776AB, category: 'language' },
            { name: 'HTML5', color: 0xE34F26, category: 'language' },
            { name: 'CSS3', color: 0x1572B6, category: 'language' },
            // Frameworks
            { name: 'React', color: 0x61DAFB, category: 'framework' },
            { name: 'Node.js', color: 0x339933, category: 'framework' },
            { name: 'Flask', color: 0x000000, category: 'framework' },
            { name: 'FastAPI', color: 0x009688, category: 'framework' },
            { name: 'Tailwind', color: 0x38B2AC, category: 'framework' },
            { name: 'Bootstrap', color: 0x7952B3, category: 'framework' },
            // Databases
            { name: 'MongoDB', color: 0x47A248, category: 'database' },
            { name: 'PostgreSQL', color: 0x316192, category: 'database' },
            { name: 'MySQL', color: 0x4479A1, category: 'database' },
            // DevOps
            { name: 'Git', color: 0xF05032, category: 'devops' },
            { name: 'GitHub', color: 0x181717, category: 'devops' },
            { name: 'GitLab', color: 0xFC6D26, category: 'devops' },
            { name: 'Vercel', color: 0x000000, category: 'devops' },
            { name: 'Vite', color: 0x646CFF, category: 'devops' },
            { name: 'npm', color: 0xCB3837, category: 'devops' },
            // AI & ML
            { name: 'Copilot', color: 0x000000, category: 'ai' },
            { name: 'Gemini', color: 0x886FBF, category: 'ai' },
            { name: 'HuggingFace', color: 0xFFD21E, category: 'ai' }
        ];
        // Scene setup
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setClearColor(0x0d1117, 0);
        renderer.shadowMap.enabled = true;
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        document.getElementById('container').appendChild(renderer.domElement);
        // Central sphere
        const sphereGeometry = new THREE.SphereGeometry(2, 32, 32);
        const sphereMaterial = new THREE.MeshPhongMaterial({
            color: 0x58a6ff,
            transparent: true,
            opacity: 0.3,
            wireframe: true
        });
        const centralSphere = new THREE.Mesh(sphereGeometry, sphereMaterial);
        scene.add(centralSphere);
        // Core glowing sphere
        const coreGeometry = new THREE.SphereGeometry(1.5, 32, 32);
        const coreMaterial = new THREE.MeshPhongMaterial({
            color: 0x58a6ff,
            transparent: true,
            opacity: 0.1,
        });
        const coreSphere = new THREE.Mesh(coreGeometry, coreMaterial);
        scene.add(coreSphere);
        // Tech nodes
        const techNodes = [];
        const techGroup = new THREE.Group();
        techStack.forEach((tech, index) => {
            // Create tech node
            const nodeGeometry = new THREE.SphereGeometry(0.15, 16, 16);
            const nodeMaterial = new THREE.MeshPhongMaterial({
                color: tech.color,
                emissive: tech.color,
                emissiveIntensity: 0.2
            });
            const node = new THREE.Mesh(nodeGeometry, nodeMaterial);
            // Position nodes in spherical distribution
            const phi = Math.acos(-1 + (2 * index) / techStack.length);
            const theta = Math.sqrt(techStack.length * Math.PI) * phi;
            const radius = 4 + Math.random() * 2;
            node.position.setFromSphericalCoords(radius, phi, theta);
            // Create glow effect
            const glowGeometry = new THREE.SphereGeometry(0.25, 16, 16);
            const glowMaterial = new THREE.MeshBasicMaterial({
                color: tech.color,
                transparent: true,
                opacity: 0.3
            });
            const glow = new THREE.Mesh(glowGeometry, glowMaterial);
            glow.position.copy(node.position);
            // Add connecting line to center
            const lineGeometry = new THREE.BufferGeometry().setFromPoints([
                new THREE.Vector3(0, 0, 0),
                node.position.clone().normalize().multiplyScalar(2)
            ]);
            const lineMaterial = new THREE.LineBasicMaterial({
                color: tech.color,
                transparent: true,
                opacity: 0.3
            });
            const line = new THREE.Line(lineGeometry, lineMaterial);
            techGroup.add(node);
            techGroup.add(glow);
            techGroup.add(line);
            techNodes.push({ node, glow, tech, originalPosition: node.position.clone() });
        });
        scene.add(techGroup);
        // Lighting
        const ambientLight = new THREE.AmbientLight(0x404040, 0.4);
        scene.add(ambientLight);
        const directionalLight = new THREE.DirectionalLight(0x58a6ff, 0.8);
        directionalLight.position.set(10, 10, 5);
        directionalLight.castShadow = true;
        scene.add(directionalLight);
        const pointLight = new THREE.PointLight(0x58a6ff, 0.5, 100);
        pointLight.position.set(0, 0, 0);
        scene.add(pointLight);
        // Particle system for background stars
        const starsGeometry = new THREE.BufferGeometry();
        const starsCount = 1000;
        const starsPositions = new Float32Array(starsCount * 3);
        for (let i = 0; i < starsCount * 3; i++) {
            starsPositions[i] = (Math.random() - 0.5) * 100;
        }
        starsGeometry.setAttribute('position', new THREE.BufferAttribute(starsPositions, 3));
        const starsMaterial = new THREE.PointsMaterial({
            color: 0x58a6ff,
            size: 0.02,
            transparent: true,
            opacity: 0.8
        });
        const stars = new THREE.Points(starsGeometry, starsMaterial);
        scene.add(stars);
        // Camera position
        camera.position.set(0, 0, 8);
        // Mouse controls
        let mouseX = 0, mouseY = 0;
        let targetRotationX = 0, targetRotationY = 0;
        let isMouseDown = false;
        document.addEventListener('mousedown', () => isMouseDown = true);
        document.addEventListener('mouseup', () => isMouseDown = false);
        document.addEventListener('mousemove', (event) => {
            if (isMouseDown) {
                mouseX = (event.clientX / window.innerWidth) * 2 - 1;
                mouseY = -(event.clientY / window.innerHeight) * 2 + 1;
                targetRotationY = mouseX * 0.5;
                targetRotationX = mouseY * 0.5;
            }
        });
        // Zoom control
        document.addEventListener('wheel', (event) => {
            camera.position.z += event.deltaY * 0.01;
            camera.position.z = Math.max(5, Math.min(15, camera.position.z));
        });
        // Animation
        let time = 0;
        function animate() {
            requestAnimationFrame(animate);
            time += 0.01;
            // Rotate central sphere
            centralSphere.rotation.y += 0.005;
            coreSphere.rotation.x += 0.003;
            coreSphere.rotation.y -= 0.004;
            // Animate tech nodes
            techNodes.forEach((item, index) => {
                const { node, glow, originalPosition } = item;  
                // Orbital motion
                const orbitSpeed = 0.002 + (index % 3) * 0.001;
                const orbitRadius = 4 + Math.sin(time + index) * 0.5;
                const angle = time * orbitSpeed + (index * Math.PI * 2) / techNodes.length;
                const x = Math.cos(angle) * orbitRadius * Math.cos(index);
                const y = Math.sin(time * 0.5 + index) * 2;
                const z = Math.sin(angle) * orbitRadius * Math.sin(index);
                node.position.set(x, y, z);
                glow.position.copy(node.position);
                // Pulse effect
                const pulse = 1 + Math.sin(time * 2 + index) * 0.2;
                node.scale.setScalar(pulse);
                glow.scale.setScalar(pulse * 1.2);
            });
            // Smooth camera rotation
            if (!isMouseDown) {
                targetRotationY += 0.002;
            }
            techGroup.rotation.y += (targetRotationY - techGroup.rotation.y) * 0.05;
            techGroup.rotation.x += (targetRotationX - techGroup.rotation.x) * 0.05;
            // Stars rotation
            stars.rotation.y += 0.0005;
            renderer.render(scene, camera);
        }
        // Handle window resize
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });
        // Hide loading screen
        setTimeout(() => {
            document.getElementById('loading').style.display = 'none';
        }, 1000);
        // Start animation
        animate();
    </script>
</body>
</html>
