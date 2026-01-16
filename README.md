# -Daenerys<div id="ai-bio" style="width:100%;height:500px;position:relative;overflow:hidden;border-radius:20px;background:linear-gradient(135deg,#0a0a0a 0%,#1a0033 50%,#000 100%);box-shadow:0 20px 40px rgba(0,255,255,0.1);">
  <canvas id="three-canvas"></canvas>
  <div style="position:absolute;top:20px;left:20px;color:#00ffff;font-family:'Courier New',monospace;font-size:24px;font-weight:bold;text-shadow:0 0 10px #00ffff;z-index:10;">
    AI/ML Engineer in Training
  </div>
  <div style="position:absolute;bottom:20px;left:20px;right:20px;color:#ffffff;font-family:'Courier New',monospace;font-size:16px;line-height:1.4;text-shadow:0 0 5px #00ff88;z-index:10;">
    🚀 2nd-year B.Tech CSE | AI/ML Specialist<br>
    Building neural nets, full-stack apps & optimized systems.<br>
    Java | HTML/JS | DS/Algo | OS | ML Frameworks<br>
    Bhopal, IN • Streaming code & lifts • Open to collabs!
  </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(75, window.innerWidth / 500, 0.1, 1000);
  const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById('three-canvas'), alpha: true });
  renderer.setSize(window.innerWidth, 500);
  renderer.setClearColor(0x000000, 0);

  // AI Core (glowing sphere)
  const coreGeometry = new THREE.SphereGeometry(1, 32, 32);
  const coreMaterial = new THREE.MeshBasicMaterial({ color: 0x00ffff, wireframe: true });
  const core = new THREE.Mesh(coreGeometry, coreMaterial);
  scene.add(core);

  // Neural particles
  const particles = new THREE.BufferGeometry();
  const particleCount = 200;
  const positions = new Float32Array(particleCount * 3);
  const colors = new Float32Array(particleCount * 3);

  for (let i = 0; i < particleCount; i++) {
    positions[i * 3] = (Math.random() - 0.5) * 10;
    positions[i * 3 + 1] = (Math.random() - 0.5) * 10;
    positions[i * 3 + 2] = (Math.random() - 0.5) * 10;
    colors[i * 3] = Math.random();
    colors[i * 3 + 1] = Math.random();
    colors[i * 3 + 2] = 1;
  }

  particles.setAttribute('position', new THREE.BufferAttribute(positions, 3));
  particles.setAttribute('color', new THREE.BufferAttribute(colors, 3));

  const particleMaterial = new THREE.PointsMaterial({ size: 0.05, vertexColors: true });
  const particleSystem = new THREE.Points(particles, particleMaterial);
  scene.add(particleSystem);

  // Lines connecting nodes (neural links)
  const lineMaterial = new THREE.LineBasicMaterial({ color: 0x00ff88, opacity: 0.3, transparent: true });
  for (let i = 0; i < 50; i++) {
    const points = [
      new THREE.Vector3((Math.random()-0.5)*8, (Math.random()-0.5)*8, (Math.random()-0.5)*8),
      new THREE.Vector3((Math.random()-0.5)*8, (Math.random()-0.5)*8, (Math.random()-0.5)*8)
    ];
    const lineGeometry = new THREE.BufferGeometry().setFromPoints(points);
    const line = new THREE.Line(lineGeometry, lineMaterial);
    scene.add(line);
  }

  camera.position.z = 5;

  function animate() {
    requestAnimationFrame(animate);
    core.rotation.y += 0.01;
    particleSystem.rotation.y += 0.005;
    particleSystem.rotation.x += 0.002;
    renderer.render(scene, camera);
  }
  animate();

  window.addEventListener('resize', () => {
    camera.aspect = window.innerWidth / 500;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, 500);
  });
</script>
