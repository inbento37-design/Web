<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Finanzas • Suscripción + Descarga</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    *{font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Cantarell,'Helvetica Neue',Arial,'Noto Sans',sans-serif}
  </style>
</head>
<body class="bg-stone-50 text-stone-900">
  <header class="sticky top-0 z-40 bg-white/90 backdrop-blur border-b border-stone-200">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 py-3 flex items-center gap-4">
      <span class="text-xl font-extrabold tracking-tight">DINERO • Blog</span>
      <button id="open-sub-modal" class="ml-auto rounded-2xl px-4 py-2 bg-stone-900 text-white text-sm font-semibold shadow">Suscribirse</button>
    </div>
  </header>

  <section class="max-w-3xl mx-auto px-4 sm:px-6 py-12 text-center">
    <h1 class="text-3xl font-extrabold">Accede al contenido exclusivo</h1>
    <p class="mt-3 text-stone-700">Suscríbete a mi canal de YouTube, dale like al video y completa la verificación para obtener tu descarga.</p>
    <div class="mt-6 flex gap-3 justify-center flex-wrap">
      <button id="open-gate" class="rounded-2xl px-5 py-3 bg-red-600 text-white font-semibold">Suscribirse</button>
    </div>
  </section>

  <!-- Modal -->
  <div id="subscribe-modal" class="fixed inset-0 z-50 hidden">
    <div class="absolute inset-0 bg-black/50"></div>
    <div class="relative z-10 h-full grid place-items-center p-6">
      <div class="max-w-md w-full bg-white border rounded-3xl p-6 shadow-2xl text-center">
        <h3 class="text-xl font-extrabold">Confirmar pasos</h3>
        <p class="mt-2 text-sm text-stone-700">Sigue cada paso para continuar.</p>

        <!-- Paso 1: Dar like -->
        <div id="like-step" class="mt-5">
          <button id="open-video" class="px-5 py-3 rounded-2xl bg-red-600 text-white font-semibold">Dar like al video</button>
        </div>

        <!-- Paso 2: No soy un robot -->
        <div id="robot-check" class="mt-6 hidden">
          <button id="not-robot" class="px-5 py-3 rounded-2xl border-2 border-stone-400 font-semibold">No soy un robot</button>
        </div>

        <!-- Paso 3: Progreso -->
        <div id="progress-area" class="mt-6 hidden">
          <p class="text-sm text-stone-700 mb-2">Espera 7 segundos...</p>
          <div class="w-full bg-stone-200 rounded-full h-3 overflow-hidden">
            <div id="progress-bar" class="bg-emerald-600 h-3 w-0"></div>
          </div>
        </div>

        <!-- Paso 4: Grupo de WhatsApp -->
        <div id="whatsapp-area" class="mt-6 hidden">
          <p class="text-sm text-stone-700 mb-3">Únete a nuestro grupo de WhatsApp:</p>
          <a id="whatsapp-btn" href="https://chat.whatsapp.com/HkmNRGbee4x4hDOmCBNfAN?mode=ems_copy_c" target="_blank" rel="noopener" class="px-5 py-3 rounded-2xl bg-green-600 text-white font-semibold">Unirme al grupo</a>
          <div class="mt-4 hidden" id="continue-wrapper">
            <button id="continue-btn" class="px-5 py-3 rounded-2xl bg-blue-600 text-white font-semibold">Seguir</button>
          </div>
        </div>

        <!-- Paso 5: Descarga final -->
        <div id="download-area" class="mt-6 hidden">
          <p class="text-sm text-stone-700">¡Listo! Ahora puedes descargar:</p>
          <a href="https://www.mediafire.com/file/2hktzpdapr2q8hb/aimbot+disimulado.7z/file" 
             target="_blank" rel="noopener" 
             class="mt-3 inline-block px-5 py-3 rounded-2xl bg-emerald-600 text-white font-semibold">
             Descargar ahora
          </a>
        </div>
      </div>
    </div>
  </div>

  <script>
    const modal = document.getElementById('subscribe-modal');
    const openGateBtn = document.getElementById('open-gate');
    const openVideoBtn = document.getElementById('open-video');
    const robotCheck = document.getElementById('robot-check');
    const notRobotBtn = document.getElementById('not-robot');
    const progressArea = document.getElementById('progress-area');
    const progressBar = document.getElementById('progress-bar');
    const whatsappArea = document.getElementById('whatsapp-area');
    const whatsappBtn = document.getElementById('whatsapp-btn');
    const continueWrapper = document.getElementById('continue-wrapper');
    const continueBtn = document.getElementById('continue-btn');
    const downloadArea = document.getElementById('download-area');

    function showModal(){ modal.classList.remove('hidden'); }

    openGateBtn.addEventListener('click', () => { 
      showModal(); 
      window.open('https://www.youtube.com/@jk-trick2625', '_blank'); 
    });
    document.getElementById('open-sub-modal').addEventListener('click', () => { 
      showModal(); 
      window.open('https://www.youtube.com/@jk-trick2625', '_blank'); 
    });

    openVideoBtn.addEventListener('click', () => {
      window.open('https://www.youtube.com/watch?v=VIDEO_ID', '_blank'); // Cambia VIDEO_ID por tu video
      robotCheck.classList.remove('hidden');
    });

    notRobotBtn.addEventListener('click', () => {
      robotCheck.classList.add('hidden');
      progressArea.classList.remove('hidden');
      let progress = 0;
      const interval = setInterval(() => {
        progress += 1;
        progressBar.style.width = progress + '%';
        if(progress >= 100){
          clearInterval(interval);
          progressArea.classList.add('hidden');
          whatsappArea.classList.remove('hidden');
        }
      }, 70); // 7 segundos
    });

    whatsappBtn.addEventListener('click', () => {
      continueWrapper.classList.remove('hidden');
    });

    continueBtn.addEventListener('click', () => {
      whatsappArea.classList.add('hidden');
      downloadArea.classList.remove('hidden');
    });
  </script>
</body>
</html>
