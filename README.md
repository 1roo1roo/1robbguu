```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>1RO B. BGU • Portal Académico Oficial 2026</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Space+Grotesk:wght@500;600;700&family=Syne:wght@700;800&display=swap" rel="stylesheet">

  <style>
    :root {
      --ease-studio: cubic-bezier(0.22, 1, 0.36, 1);
      --speed-fast: 0.25s;
      --neon-cyan-green: #00F5D4;
      --neon-green: #00FF87;
      --neon-blue: #00B4D8;
      --glass-alpha: 0.14;
      --glass-glow: 0.50;
      --glass-blur: 14px;
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      padding: 0;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
      background-color: #070B10;
      color: #FFFFFF;
      overflow-x: hidden;
      min-height: 100vh;
    }

    .font-display {
      font-family: 'Syne', 'Space Grotesk', sans-serif;
      letter-spacing: -0.04em;
    }

    .font-tech {
      font-family: 'Space Grotesk', sans-serif;
    }

    /* ==================== FONDO ARQUITECTÓNICO & WALLPAPER GPU ==================== */
    #app-wallpaper {
      position: fixed;
      inset: 0;
      z-index: 0;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      transform: translate3d(0, 0, 0);
      transition: background-image var(--speed-fast) var(--ease-studio), filter var(--speed-fast) var(--ease-studio);
      will-change: background-image;
    }

    #architectural-grid {
      position: fixed;
      inset: 0;
      z-index: 1;
      background-image:
        linear-gradient(to right, rgba(255, 255, 255, 0.04) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(255, 255, 255, 0.04) 1px, transparent 1px);
      background-size: 64px 64px;
      pointer-events: none;
    }

    #wallpaper-vignette {
      position: fixed;
      inset: 0;
      z-index: 2;
      background:
        radial-gradient(circle at 50% 0%, rgba(0, 245, 212, 0.10), transparent 62%),
        linear-gradient(180deg, rgba(7, 11, 16, 0.25) 0%, rgba(7, 11, 16, 0.72) 100%);
      pointer-events: none;
    }

    /* ==================== SHOWREEL ENTRADA 'WEBSITES IN 2026' (CANVAS 2D 60FPS) ==================== */
    #intro-showreel {
      position: fixed;
      inset: 0;
      z-index: 9999;
      background: #070B10;
      overflow: hidden;
      transform: translate3d(0, 0, 0);
      transition: clip-path 0.35s var(--ease-studio), opacity 0.25s var(--ease-studio), transform 0.35s var(--ease-studio);
      clip-path: inset(0% 0% 0% 0%);
      will-change: clip-path, opacity, transform;
    }

    #intro-showreel.reel-exit {
      clip-path: inset(0% 0% 100% 0%);
      opacity: 0.2;
      pointer-events: none;
    }

    #showreel-canvas {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      display: block;
    }

    .reel-precision-hairline {
      position: absolute;
      background: linear-gradient(90deg, transparent, rgba(0, 245, 212, 0.55), rgba(255, 255, 255, 0.85), rgba(0, 180, 216, 0.55), transparent);
      pointer-events: none;
    }

    .btn-enter-portal {
      background: #FFFFFF;
      color: #070B10;
      border: 1px solid #FFFFFF;
      box-shadow:
        0 0 0 1px rgba(0, 245, 212, 0.45),
        0 14px 36px rgba(0, 245, 212, 0.28),
        -2px 0 0 rgba(0, 245, 212, 0.8),
        2px 0 0 rgba(0, 180, 216, 0.8);
      transform: translate3d(0, 0, 0);
      transition: transform var(--speed-fast) var(--ease-studio), background var(--speed-fast) var(--ease-studio), box-shadow var(--speed-fast) var(--ease-studio);
    }

    .btn-enter-portal:hover {
      background: #00F5D4;
      border-color: #00F5D4;
      color: #070B10;
      transform: translate3d(0, -2px, 0) scale(1.02);
      box-shadow:
        0 18px 44px rgba(0, 245, 212, 0.45),
        -3px 0 0 rgba(0, 255, 135, 0.9),
        3px 0 0 rgba(0, 180, 216, 0.9);
    }

    .btn-enter-portal:active {
      transform: translate3d(0, 0, 0) scale(0.97);
    }

    /* ==================== LIQUID GLASS 60FPS CON BRILLOS 0.25s ==================== */
    .liquid-panel {
      position: relative;
      background: rgba(7, 11, 16, calc(0.46 + var(--glass-alpha)));
      backdrop-filter: blur(var(--glass-blur)) saturate(165%);
      -webkit-backdrop-filter: blur(var(--glass-blur)) saturate(165%);
      border: 1px solid rgba(255, 255, 255, 0.18);
      box-shadow:
        0 12px 32px rgba(0, 0, 0, 0.38),
        inset 0 1px 0 rgba(255, 255, 255, 0.45),
        inset 0 -1px 0 rgba(0, 245, 212, 0.2),
        -1px 0 0 rgba(0, 245, 212, var(--glass-glow)),
        1px 0 0 rgba(0, 180, 216, var(--glass-glow));
      transform: translate3d(0, 0, 0);
      transition: transform var(--speed-fast) var(--ease-studio), border-color var(--speed-fast) var(--ease-studio), box-shadow var(--speed-fast) var(--ease-studio);
    }

    .liquid-card {
      position: relative;
      overflow: hidden;
      background: linear-gradient(150deg, rgba(255, 255, 255, calc(0.07 + var(--glass-alpha))) 0%, rgba(7, 11, 16, 0.72) 100%);
      border: 1px solid rgba(255, 255, 255, 0.16);
      box-shadow:
        0 8px 24px rgba(0, 0, 0, 0.3),
        inset 0 1px 0 rgba(255, 255, 255, 0.4),
        -1px 0 0 rgba(0, 245, 212, 0.35),
        1px 0 0 rgba(0, 180, 216, 0.35);
      transform: translate3d(0, 0, 0);
      transition: transform var(--speed-fast) var(--ease-studio), border-color var(--speed-fast) var(--ease-studio), box-shadow var(--speed-fast) var(--ease-studio);
    }

    /* Reflejo especular suave en 0.25s al pasar/tocar */
    .liquid-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(115deg, transparent 20%, rgba(0, 245, 212, 0.14) 48%, rgba(255, 255, 255, 0.22) 52%, transparent 80%);
      transform: translate3d(-120%, 0, 0);
      transition: transform var(--speed-fast) var(--ease-studio);
      pointer-events: none;
    }

    .liquid-card:hover {
      transform: translate3d(0, -2px, 0);
      border-color: rgba(0, 245, 212, 0.6);
      box-shadow:
        0 14px 32px rgba(0, 0, 0, 0.4),
        inset 0 1px 0 rgba(255, 255, 255, 0.65),
        -1.5px 0 0 rgba(0, 255, 135, 0.7),
        1.5px 0 0 rgba(0, 180, 216, 0.7);
    }

    .liquid-card:hover::after {
      transform: translate3d(120%, 0, 0);
    }

    .glass-btn {
      background: rgba(255, 255, 255, 0.08);
      border: 1px solid rgba(255, 255, 255, 0.2);
      box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.32);
      color: #FFFFFF;
      transform: translate3d(0, 0, 0);
      transition: transform var(--speed-fast) var(--ease-studio), background var(--speed-fast) var(--ease-studio), border-color var(--speed-fast) var(--ease-studio), color var(--speed-fast) var(--ease-studio);
    }

    .glass-btn:hover {
      background: rgba(255, 255, 255, 0.16);
      border-color: rgba(0, 245, 212, 0.55);
    }

    .glass-btn:active {
      transform: translate3d(0, 0, 0) scale(0.96);
    }

    .glass-btn.active {
      background: #FFFFFF;
      color: #070B10;
      border-color: #FFFFFF;
      font-weight: 800;
      box-shadow:
        0 4px 16px rgba(0, 245, 212, 0.28),
        -1.5px 0 0 rgba(0, 245, 212, 0.85),
        1.5px 0 0 rgba(0, 180, 216, 0.85);
    }

    .studio-input {
      background: rgba(7, 11, 16, 0.72);
      border: 1px solid rgba(255, 255, 255, 0.22);
      color: #FFFFFF;
      transition: border-color var(--speed-fast) var(--ease-studio), box-shadow var(--speed-fast) var(--ease-studio);
    }

    .studio-input:focus {
      outline: none;
      border-color: #00F5D4;
      box-shadow: 0 0 0 2px rgba(0, 245, 212, 0.22);
    }

    .studio-input::placeholder {
      color: rgba(255, 255, 255, 0.45);
    }

    .tag-evaluacion {
      display: inline-block;
      background: #00F5D4;
      color: #041311;
      font-weight: 800;
      padding: 1px 6px;
      border-radius: 4px;
      font-size: 10px;
      letter-spacing: 0.01em;
      box-shadow: 0 0 10px rgba(0, 245, 212, 0.35);
    }

    .fade-slide-in {
      animation: fadeSlideIn var(--speed-fast) var(--ease-studio) forwards;
    }

    @keyframes fadeSlideIn {
      from { opacity: 0; transform: translate3d(0, 8px, 0); }
      to { opacity: 1; transform: translate3d(0, 0, 0); }
    }

    ::-webkit-scrollbar { width: 5px; height: 5px; }
    ::-webkit-scrollbar-track { background: rgba(7, 11, 16, 0.45); }
    ::-webkit-scrollbar-thumb { background: rgba(0, 245, 212, 0.35); border-radius: 99px; }
    ::-webkit-scrollbar-thumb:hover { background: rgba(0, 245, 212, 0.65); }
  </style>
</head>
<body class="antialiased selection:bg-[#00F5D4] selection:text-[#070B10]">

  <!-- ==================== CAPAS DE FONDO GPU ==================== -->
  <div id="app-wallpaper"></div>
  <div id="architectural-grid"></div>
  <div id="wallpaper-vignette"></div>

  <!-- ==================== 1. PANTALLA DE ENTRADA SHOWREEL 'WEBSITES IN 2026' (CANVAS 2D 60FPS) ==================== -->
  <section id="intro-showreel" aria-label="Entrada Showreel 2026">
    <canvas id="showreel-canvas"></canvas>
    <div class="reel-precision-hairline top-14 inset-x-0 h-[1px]"></div>
    <div class="reel-precision-hairline bottom-14 inset-x-0 h-[1px]"></div>

    <!-- Barra Superior de Entrada -->
    <div class="relative z-10 max-w-7xl w-full mx-auto px-5 sm:px-8 pt-4 flex items-center justify-between text-[11px] font-tech uppercase tracking-[0.2em] text-white/80">
      <div class="flex items-center gap-2.5">
        <span class="w-2 h-2 rounded-full bg-[#00FF87]"></span>
        <span>WEBSITES IN 2026 // 1RO B. BGU</span>
      </div>
      <div class="flex items-center gap-3">
        <span id="reel-visits-badge" class="hidden sm:inline text-[#00F5D4] font-bold">VISITAS: ...</span>
        <button id="btn-skip-reel" type="button" class="glass-btn px-3.5 py-1.5 rounded-full text-[10px] font-tech font-bold uppercase tracking-widest cursor-pointer">
          Saltar / Entrar →
        </button>
      </div>
    </div>

    <!-- Centro Editorial de Alta Precisión -->
    <div class="relative z-10 max-w-6xl w-full mx-auto px-5 sm:px-8 my-auto py-8 flex flex-col justify-between h-[72vh]">
      <div class="space-y-2">
        <div class="inline-flex items-center gap-2 px-3.5 py-1 rounded-full border border-white/20 bg-black/50 backdrop-blur-md">
          <span class="w-1.5 h-1.5 rounded-full bg-[#00F5D4]"></span>
          <span class="text-[10px] sm:text-[11px] font-tech uppercase tracking-[0.22em] text-white/90">
            BACHILLERATO GENERAL UNIFICADO • PARALELO B
          </span>
        </div>
        <div id="reel-scene-label" class="text-[11px] font-tech uppercase tracking-[0.25em] text-[#00FF87] pt-1">
          ESCENA 01 // ARQUITECTURA DE PRECISIÓN
        </div>
      </div>

      <div class="space-y-5">
        <h1 class="font-display text-5xl sm:text-7xl md:text-[7.2rem] font-extrabold leading-[0.88] tracking-tight text-white uppercase">
          1RO B.<br/>
          <span class="text-transparent bg-clip-text bg-gradient-to-r from-[#00F5D4] via-[#00FF87] to-[#00B4D8]">
            BGU 2026
          </span>
        </h1>

        <div class="flex flex-col md:flex-row md:items-end justify-between gap-5 pt-4 border-t border-white/15">
          <div class="space-y-1 max-w-xl">
            <p class="font-tech text-xs sm:text-sm uppercase tracking-[0.16em] text-[#00F5D4] font-bold">
              TUTORA: LCDA. ALEJANDRA SABANDO PONCE • BGU 1B
            </p>
            <p class="text-xs sm:text-sm text-white/80 leading-relaxed">
              Horario matricial oficial, tareas, exposiciones, materiales y recursos visuales en tiempo real con fluidez 60fps.
            </p>
          </div>

          <button id="btn-enter-portal" type="button" class="btn-enter-portal px-8 py-4 sm:px-10 sm:py-5 rounded-full font-tech font-extrabold text-xs sm:text-sm uppercase tracking-[0.2em] flex items-center justify-center gap-3 cursor-pointer shrink-0">
            <span>ENTRAR AL PORTAL</span>
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13 7l5 5m0 0l-5 5m5-5H6" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Pie de Showreel -->
    <div class="relative z-10 max-w-7xl w-full mx-auto px-5 sm:px-8 pb-4 flex items-center justify-between text-[10px] font-tech uppercase tracking-[0.2em] text-white/55">
      <span>LIQUID GLASS ENGINE • 60FPS GPU</span>
      <button id="btn-replay-reel" type="button" class="hover:text-[#00F5D4] transition-colors cursor-pointer">
        REINICIAR SECUENCIA
      </button>
    </div>
  </section>

  <!-- ==================== 2. PLATAFORMA PRINCIPAL ==================== -->
  <div id="main-app" class="relative z-10 min-h-screen flex flex-col">

    <!-- HEADER SUPERIOR -->
    <header class="sticky top-0 z-40 px-3 sm:px-6 pt-3 pb-2">
      <div class="max-w-7xl mx-auto liquid-panel rounded-2xl px-4 py-3 sm:px-5 flex flex-wrap items-center justify-between gap-3">

        <!-- Marca del Curso -->
        <div class="flex items-center gap-3">
          <button id="btn-open-reel" type="button" title="Ver showreel de entrada 2026" class="w-10 h-10 rounded-xl bg-white text-[#070B10] font-display font-extrabold text-sm flex items-center justify-center hover:bg-[#00F5D4] transition-colors cursor-pointer shrink-0">
            1B
          </button>
          <div>
            <div class="flex items-center gap-2">
              <span class="font-display font-extrabold text-base sm:text-lg tracking-tight text-white">1RO B. BGU</span>
              <span id="badge-mode" class="text-[10px] font-tech font-bold uppercase tracking-wider px-2 py-0.5 rounded-md bg-white/10 border border-white/20 text-[#00F5D4]">
                Modo Espectador
              </span>
            </div>
            <p class="text-[11px] text-white/75 truncate max-w-[210px] sm:max-w-none">
              Tutora: Lcda. Alejandra Sabando Ponce (BGU 1B)
            </p>
          </div>
        </div>

        <!-- Controles Derecha -->
        <div class="flex items-center gap-2 ml-auto">

          <!-- Contador de Visitas Persistente + Desglose -->
          <div class="glass-btn px-3 py-1.5 rounded-xl flex items-center gap-2" title="Contador de visitas y publicaciones">
            <span class="w-2 h-2 rounded-full bg-[#00FF87]"></span>
            <div class="leading-tight">
              <span class="block text-[9px] font-tech uppercase tracking-wider text-white/60">
                Visitas • <span id="stat-posts-mini" class="text-[#00F5D4]">0</span> pub.
              </span>
              <span id="live-visits-count" class="text-xs sm:text-sm font-tech font-bold text-white tabular-nums">...</span>
            </div>
            <button id="btn-refresh-visits" type="button" title="Actualizar contador" class="p-1 text-white/65 hover:text-[#00F5D4] transition-colors cursor-pointer">
              <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" stroke-width="2.2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
              </svg>
            </button>
          </div>

          <!-- Botón Estudio Editor Pro (Solo desbloqueado) -->
          <button id="btn-editor-studio" type="button" class="hidden glass-btn px-3 py-2 rounded-xl items-center gap-1.5 text-xs font-bold text-[#00F5D4] border-[#00F5D4]/45 cursor-pointer">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4" />
            </svg>
            <span class="hidden md:inline">Editor Pro</span>
          </button>

          <!-- Botón Nueva Publicación (Solo desbloqueado) -->
          <button id="btn-new-task" type="button" class="hidden bg-[#00F5D4] hover:bg-[#00FF87] text-[#070B10] px-3.5 py-2 rounded-xl items-center gap-1.5 text-xs font-extrabold transition-colors cursor-pointer">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 4v16m8-8H4" />
            </svg>
            <span>Publicar</span>
          </button>

          <!-- Botón Llave Editor -->
          <button id="btn-key-modal" type="button" class="glass-btn px-3 py-2 rounded-xl flex items-center gap-1.5 text-xs font-bold cursor-pointer">
            <svg id="icon-lock" class="w-4 h-4 text-[#00F5D4]" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 7a2 2 0 012 2m4 0a6 6 0 01-7.743 5.743L11 17H9v2H7v2H4a1 1 0 01-1-1v-2.586a1 1 0 01.293-.707l5.964-5.964A6 6 0 1121 9z" />
            </svg>
            <svg id="icon-unlock" class="w-4 h-4 text-[#00FF87] hidden" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M8 11V7a4 4 0 118 0m-4 8v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2z" />
            </svg>
            <span id="label-key-btn" class="hidden sm:inline">Llave Editor</span>
          </button>
        </div>
      </div>
    </header>

    <!-- CONTENIDO PRINCIPAL -->
    <main class="flex-1 max-w-7xl w-full mx-auto px-3 sm:px-6 py-3 space-y-4">

      <!-- AVISO GLOBAL DE LA TUTORA / CURSO -->
      <div id="pinned-banner" class="hidden liquid-panel rounded-2xl px-4 py-3 border-l-4 border-l-[#00FF87] flex items-center justify-between gap-3 fade-slide-in">
        <div class="flex items-center gap-3">
          <span class="px-2 py-0.5 rounded bg-[#00FF87] text-[#070B10] font-tech font-extrabold text-[10px] uppercase tracking-wider shrink-0">
            AVISO TUTORA / CURSO
          </span>
          <p id="pinned-banner-text" class="text-xs sm:text-sm font-semibold text-white"></p>
        </div>
        <button id="btn-edit-banner-inline" type="button" class="hidden text-xs font-bold text-[#00F5D4] hover:underline shrink-0 cursor-pointer">
          Editar aviso
        </button>
      </div>

      <!-- NAVEGACIÓN + PROGRESO + BUSCADOR -->
      <div class="flex flex-col lg:flex-row lg:items-center justify-between gap-3">
        <div class="flex flex-wrap items-center gap-2">
          <div class="liquid-panel p-1 rounded-xl inline-flex items-center gap-1">
            <button type="button" data-view="tareas" class="nav-view-btn glass-btn active px-4 py-2 rounded-lg text-xs font-bold flex items-center gap-2 cursor-pointer">
              <span>Publicaciones</span>
              <span id="badge-tasks-count" class="px-1.5 py-0.2 rounded bg-black/25 text-[11px] font-tech">0</span>
            </button>
            <button type="button" data-view="horario" class="nav-view-btn glass-btn px-4 py-2 rounded-lg text-xs font-bold flex items-center gap-2 cursor-pointer">
              <span>Horario Oficial BGU 1B</span>
            </button>
          </div>

          <!-- Progreso del Estudiante -->
          <div class="liquid-panel px-3.5 py-2 rounded-xl flex items-center gap-2.5">
            <span class="text-[11px] font-tech uppercase tracking-wider text-white/70">Completado:</span>
            <div class="w-20 h-2 rounded-full bg-white/15 overflow-hidden">
              <div id="student-progress-bar" class="h-full bg-gradient-to-r from-[#00F5D4] to-[#00FF87] transition-all duration-300" style="width: 0%;"></div>
            </div>
            <span id="student-progress-text" class="text-xs font-tech font-bold text-[#00FF87]">0%</span>
          </div>
        </div>

        <!-- Buscador -->
        <div class="relative w-full lg:w-72">
          <input id="input-search" type="text" placeholder="Buscar materia, docente o tema..." class="studio-input w-full pl-9 pr-4 py-2 rounded-xl text-xs" />
          <svg class="w-4 h-4 text-white/50 absolute left-3 top-1/2 -translate-y-1/2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
          </svg>
        </div>
      </div>

      <!-- ==================== VISTA A: TAREAS, EXPOSICIONES, MATERIALES, EVALUACIÓN / AVISO ==================== -->
      <section id="section-tareas" class="space-y-4">

        <!-- Filtros por Día y Tipo -->
        <div class="liquid-panel rounded-2xl p-3.5 sm:p-4 space-y-3">
          <div class="flex flex-wrap items-center justify-between gap-2">
            <div class="flex flex-wrap items-center gap-1.5">
              <span class="text-[10px] font-tech uppercase tracking-widest text-white/60 mr-1.5">DÍA:</span>
              <button type="button" data-filter-day="Todos" class="filter-day-btn glass-btn active px-3 py-1.5 rounded-lg text-xs cursor-pointer">Todos</button>
              <button type="button" data-filter-day="Lunes" class="filter-day-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Lunes</button>
              <button type="button" data-filter-day="Martes" class="filter-day-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Martes</button>
              <button type="button" data-filter-day="Miércoles" class="filter-day-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Miércoles</button>
              <button type="button" data-filter-day="Jueves" class="filter-day-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Jueves</button>
              <button type="button" data-filter-day="Viernes" class="filter-day-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Viernes</button>
            </div>

            <button id="btn-clear-filters" type="button" class="text-[11px] font-tech text-[#00F5D4] hover:underline cursor-pointer">
              Limpiar filtros
            </button>
          </div>

          <div class="flex flex-wrap items-center gap-1.5 pt-2.5 border-t border-white/10">
            <span class="text-[10px] font-tech uppercase tracking-widest text-white/60 mr-1.5">TIPO:</span>
            <button type="button" data-filter-cat="Todas" class="filter-cat-btn glass-btn active px-3 py-1.5 rounded-lg text-xs cursor-pointer">Todas</button>
            <button type="button" data-filter-cat="Tarea" class="filter-cat-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Tarea</button>
            <button type="button" data-filter-cat="Exposición" class="filter-cat-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Exposición</button>
            <button type="button" data-filter-cat="Materiales" class="filter-cat-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Materiales</button>
            <button type="button" data-filter-cat="Evaluación / Aviso" class="filter-cat-btn glass-btn px-3 py-1.5 rounded-lg text-xs cursor-pointer">Evaluación / Aviso</button>
          </div>
        </div>

        <!-- Cuadrícula de Publicaciones -->
        <div id="tasks-container" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4"></div>

        <!-- Estado vacío -->
        <div id="tasks-empty-state" class="hidden liquid-panel rounded-2xl p-10 text-center space-y-2">
          <p class="font-display text-lg font-bold text-white">No hay publicaciones con este filtro</p>
          <p class="text-xs text-white/65 max-w-md mx-auto">
            Cambia de día o categoría, o desbloquea el Modo Editor con la llave para agregar una publicación.
          </p>
        </div>
      </section>

      <!-- ==================== VISTA B: HORARIO MATRICIAL OFICIAL BGU 1B ==================== -->
      <section id="section-horario" class="hidden space-y-4">
        <div class="liquid-panel rounded-2xl p-4 sm:p-6 space-y-4">

          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 pb-3 border-b border-white/15">
            <div>
              <div class="flex flex-wrap items-center gap-3">
                <span class="font-display font-extrabold text-xl sm:text-2xl text-white">BGU 1B</span>
                <span class="text-xs sm:text-sm font-bold text-[#00F5D4] underline decoration-[#00F5D4]/60 underline-offset-4">
                  Tutor : LCDA ALEJANDRA SABANDO PONCE
                </span>
              </div>
              <p class="text-[11px] text-white/70 mt-1">
                Toca cualquier materia para ver o filtrar sus publicaciones. <span class="text-[#00FF87]">En Modo Editor puedes publicar directo, alternar "Evaluación" o editar la nota/etiqueta de la celda.</span>
              </p>
            </div>
            <div class="flex items-center gap-2 text-[11px]">
              <span class="tag-evaluacion">Evaluación</span>
              <span class="text-white/75">= Evaluación programada</span>
            </div>
          </div>

          <div class="overflow-x-auto rounded-xl border border-white/25 bg-[#070B10]/85">
            <table class="w-full min-w-[800px] border-collapse text-left">
              <thead>
                <tr class="bg-white/10 border-b border-white/25 text-xs font-tech uppercase tracking-wider text-white">
                  <th class="p-3 w-36 border-r border-white/20 text-center">HORA</th>
                  <th class="p-3 w-1/5 border-r border-white/20 text-center">Lunes</th>
                  <th class="p-3 w-1/5 border-r border-white/20 text-center">Martes</th>
                  <th class="p-3 w-1/5 border-r border-white/20 text-center">Miércoles</th>
                  <th class="p-3 w-1/5 border-r border-white/20 text-center">Jueves</th>
                  <th class="p-3 w-1/5 text-center">Viernes</th>
                </tr>
              </thead>
              <tbody id="matrix-schedule-body" class="divide-y divide-white/20 text-xs"></tbody>
            </table>
          </div>

        </div>
      </section>

    </main>

    <footer class="py-5 px-4 text-center text-[11px] font-tech text-white/45">
      1RO B. BGU • BGU 1B • TUTORA: LCDA. ALEJANDRA SABANDO PONCE • 60FPS SIN LAG
    </footer>
  </div>

  <!-- ==================== MODAL 1: LLAVE MODO EDITOR ==================== -->
  <div id="modal-key" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-black/75 backdrop-blur-sm">
    <div class="liquid-panel rounded-2xl max-w-md w-full p-6 space-y-5 fade-slide-in">
      <div class="flex items-center justify-between border-b border-white/15 pb-3">
        <div>
          <span class="text-[10px] font-tech uppercase tracking-widest text-[#00F5D4]">AUTENTICACIÓN DEL CURSO</span>
          <h3 class="font-display text-lg font-extrabold text-white">Llave Modo Editor Pro</h3>
        </div>
        <button type="button" data-close-modal="modal-key" class="glass-btn w-8 h-8 rounded-lg flex items-center justify-center text-xs cursor-pointer">✕</button>
      </div>

      <form id="form-key" class="space-y-4">
        <div>
          <label class="block text-xs font-semibold text-white/80 mb-1.5">Código de Acceso</label>
          <input id="input-key-code" type="password" autocomplete="off" placeholder="Ingresa la llave..." class="studio-input w-full px-4 py-3 rounded-xl text-sm font-mono tracking-widest" required />
          <p id="error-key-code" class="hidden text-xs text-rose-400 font-semibold mt-2">
            Código incorrecto. Se mantiene el Modo Espectador.
          </p>
        </div>

        <div class="flex items-center justify-end gap-2">
          <button type="button" data-close-modal="modal-key" class="glass-btn px-4 py-2.5 rounded-xl text-xs font-bold cursor-pointer">Cancelar</button>
          <button type="submit" class="bg-[#00F5D4] hover:bg-[#00FF87] text-[#070B10] font-extrabold px-5 py-2.5 rounded-xl text-xs transition-colors cursor-pointer">
            Desbloquear Editor
          </button>
        </div>
      </form>
    </div>
  </div>

  <!-- ==================== MODAL 2: CREAR / EDITAR PUBLICACIÓN ==================== -->
  <div id="modal-task" class="fixed inset-0 z-50 hidden items-center justify-center p-3 sm:p-4 bg-black/75 backdrop-blur-sm overflow-y-auto">
    <div class="liquid-panel rounded-2xl max-w-2xl w-full p-5 sm:p-6 space-y-4 my-auto fade-slide-in max-h-[92vh] overflow-y-auto">
      <div class="flex items-center justify-between border-b border-white/15 pb-3">
        <div>
          <span class="text-[10px] font-tech uppercase tracking-widest text-[#00FF87]">MODO EDITOR PRO</span>
          <h3 id="modal-task-heading" class="font-display text-lg sm:text-xl font-extrabold text-white">Nueva Publicación</h3>
        </div>
        <button type="button" data-close-modal="modal-task" class="glass-btn w-8 h-8 rounded-lg flex items-center justify-center text-xs cursor-pointer">✕</button>
      </div>

      <form id="form-task" class="space-y-3.5">
        <input type="hidden" id="field-task-id" />

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
          <div>
            <label class="block text-xs font-bold text-white/80 mb-1">Día del Horario</label>
            <select id="field-task-day" class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs font-semibold">
              <option value="Lunes">Lunes</option>
              <option value="Martes">Martes</option>
              <option value="Miércoles">Miércoles</option>
              <option value="Jueves">Jueves</option>
              <option value="Viernes">Viernes</option>
            </select>
          </div>

          <div>
            <label class="block text-xs font-bold text-white/80 mb-1">Materia y Docente</label>
            <select id="field-task-subject" class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs font-semibold"></select>
          </div>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-3 gap-3">
          <div>
            <label class="block text-xs font-bold text-white/80 mb-1">Tipo de Publicación</label>
            <select id="field-task-cat" class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs font-semibold">
              <option value="Tarea">Tarea</option>
              <option value="Exposición">Exposición</option>
              <option value="Materiales">Materiales</option>
              <option value="Evaluación / Aviso">Evaluación / Aviso</option>
            </select>
          </div>

          <div>
            <label class="block text-xs font-bold text-white/80 mb-1">Prioridad</label>
            <select id="field-task-priority" class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs font-semibold">
              <option value="Normal">Normal</option>
              <option value="Urgente">Urgente</option>
              <option value="Fijada">Fijada</option>
            </select>
          </div>

          <div>
            <label class="block text-xs font-bold text-white/80 mb-1">Fecha de Entrega</label>
            <input id="field-task-date" type="date" class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs" required />
          </div>
        </div>

        <div>
          <label class="block text-xs font-bold text-white/80 mb-1">Título</label>
          <input id="field-task-title" type="text" placeholder="Ej: Exposición sobre célula vegetal / Deber pág. 54..." class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs sm:text-sm" required />
        </div>

        <div>
          <label class="block text-xs font-bold text-white/80 mb-1">Descripción / Indicaciones</label>
          <textarea id="field-task-desc" rows="3" placeholder="Detalles de la tarea, exposición, materiales o evaluación..." class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs sm:text-sm resize-none" required></textarea>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
          <div>
            <label class="block text-xs font-bold text-white/80 mb-1">Materiales (separados por coma)</label>
            <input id="field-task-materials" type="text" placeholder="Ej: Cartulina, regla, compás..." class="studio-input w-full px-3.5 py-2 rounded-xl text-xs" />
          </div>
          <div>
            <label class="block text-xs font-bold text-white/80 mb-1">Enlace / Recurso (opcional)</label>
            <input id="field-task-link" type="url" placeholder="https://..." class="studio-input w-full px-3.5 py-2 rounded-xl text-xs" />
          </div>
        </div>

        <!-- Múltiples Fotos con Compresión Automática -->
        <div class="space-y-2">
          <label class="block text-xs font-bold text-white/80">Adjuntar Fotos (compresión automática sin lag)</label>
          <label class="glass-btn flex flex-col items-center justify-center p-3.5 rounded-xl border-dashed border border-white/35 hover:border-[#00F5D4] cursor-pointer text-center">
            <span class="text-xs font-bold text-[#00F5D4]">+ Seleccionar múltiples fotos</span>
            <span class="text-[10px] text-white/55 mt-0.5">Se optimizan automáticamente en el navegador</span>
            <input id="field-task-photos" type="file" accept="image/*" multiple class="hidden" />
          </label>
          <div id="preview-form-photos" class="grid grid-cols-4 gap-2"></div>
        </div>

        <div class="flex items-center justify-end gap-2 pt-3 border-t border-white/15">
          <button type="button" data-close-modal="modal-task" class="glass-btn px-4 py-2.5 rounded-xl text-xs font-bold cursor-pointer">Cancelar</button>
          <button type="submit" class="bg-[#00F5D4] hover:bg-[#00FF87] text-[#070B10] font-extrabold px-5 py-2.5 rounded-xl text-xs transition-colors cursor-pointer">
            Guardar Publicación
          </button>
        </div>
      </form>
    </div>
  </div>

  <!-- ==================== MODAL 3: EDITOR PRO (FONDOS, GLASS, AVISOS, HORARIO, RESPALDO) ==================== -->
  <div id="modal-editor-studio" class="fixed inset-0 z-50 hidden items-center justify-center p-3 sm:p-4 bg-black/75 backdrop-blur-sm overflow-y-auto">
    <div class="liquid-panel rounded-2xl max-w-2xl w-full p-5 sm:p-6 space-y-5 my-auto fade-slide-in max-h-[92vh] overflow-y-auto">
      <div class="flex items-center justify-between border-b border-white/15 pb-3">
        <div>
          <span class="text-[10px] font-tech uppercase tracking-widest text-[#00F5D4]">SUITE COMPLETA • LLAVE ACTIVA</span>
          <h3 class="font-display text-lg font-extrabold text-white">Editor Avanzado 1ro B. BGU</h3>
        </div>
        <button type="button" data-close-modal="modal-editor-studio" class="glass-btn w-8 h-8 rounded-lg flex items-center justify-center text-xs cursor-pointer">✕</button>
      </div>

      <!-- 1. Aviso Global de Tutora / Curso -->
      <div class="space-y-2">
        <label class="block text-xs font-bold text-[#00FF87]">1. Aviso Global de la Tutora o del Curso</label>
        <div class="flex flex-col sm:flex-row gap-2">
          <input id="input-banner-msg" type="text" placeholder="Ej: Reunión de padres o entrega de carpeta..." class="studio-input flex-1 px-3.5 py-2 rounded-xl text-xs" />
          <div class="flex gap-2">
            <button id="btn-save-banner" type="button" class="bg-[#00FF87] text-[#070B10] font-extrabold px-4 py-2 rounded-xl text-xs cursor-pointer">
              Guardar Aviso
            </button>
            <button id="btn-clear-banner" type="button" class="glass-btn px-3 py-2 rounded-xl text-xs cursor-pointer">
              Borrar
            </button>
          </div>
        </div>
      </div>

      <!-- 2. Fondo de Pantalla + Intensidad Liquid Glass -->
      <div class="space-y-3 pt-3 border-t border-white/15">
        <label class="block text-xs font-bold text-[#00F5D4]">2. Fondo de Pantalla en Vivo & Intensidad Liquid Glass</label>
        <div id="presets-wallpaper-grid" class="grid grid-cols-2 sm:grid-cols-3 gap-2.5"></div>

        <label class="glass-btn w-full py-2.5 px-4 rounded-xl flex items-center justify-center gap-2 text-xs font-bold cursor-pointer">
          <span>Subir imagen personalizada como fondo</span>
          <input id="input-custom-wallpaper" type="file" accept="image/*" class="hidden" />
        </label>

        <div class="pt-1 space-y-1.5">
          <div class="flex items-center justify-between">
            <span class="text-xs font-semibold text-white/85">Intensidad Liquid Glass</span>
            <span id="glass-intensity-val" class="text-xs font-tech font-bold text-[#00F5D4]">Medio (60fps)</span>
          </div>
          <input id="slider-glass-intensity" type="range" min="0" max="2" step="1" value="1" class="w-full accent-[#00F5D4] cursor-pointer" />
        </div>
      </div>

      <!-- 3. Respaldo JSON (Exportar / Importar) y WhatsApp -->
      <div class="space-y-2.5 pt-3 border-t border-white/15">
        <label class="block text-xs font-bold text-white">3. Respaldo del Curso (JSON) y Compartir WhatsApp</label>
        <div class="flex flex-wrap gap-2">
          <button id="btn-copy-whatsapp-summary" type="button" class="glass-btn px-3.5 py-2 rounded-xl text-xs font-bold text-[#00FF87] cursor-pointer">
            Copiar Resumen WhatsApp
          </button>
          <button id="btn-export-json" type="button" class="glass-btn px-3.5 py-2 rounded-xl text-xs font-bold text-[#00F5D4] cursor-pointer">
            Exportar JSON
          </button>
          <label class="glass-btn px-3.5 py-2 rounded-xl text-xs font-bold cursor-pointer">
            <span>Importar JSON</span>
            <input id="input-import-json" type="file" accept=".json,application/json" class="hidden" />
          </label>
        </div>
      </div>

      <!-- 4. Bloquear y volver a Modo Espectador -->
      <div class="pt-3 border-t border-white/15 flex items-center justify-between gap-2">
        <span class="text-[11px] text-white/60">¿Terminaste de editar?</span>
        <button id="btn-lock-from-studio" type="button" class="glass-btn px-4 py-2 rounded-xl text-xs font-bold text-rose-300 border-rose-400/40 cursor-pointer">
          Bloquear • Modo Espectador
        </button>
      </div>
    </div>
  </div>

  <!-- ==================== MODAL 4: NOTA RÁPIDA DE CELDA DEL HORARIO (EDITOR) ==================== -->
  <div id="modal-cell-note" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-black/75 backdrop-blur-sm">
    <div class="liquid-panel rounded-2xl max-w-md w-full p-5 space-y-4 fade-slide-in">
      <div class="flex items-center justify-between border-b border-white/15 pb-2.5">
        <div>
          <span class="text-[10px] font-tech uppercase tracking-widest text-[#00F5D4]">HORARIO BGU 1B</span>
          <h3 id="cell-note-title" class="font-display text-base font-extrabold text-white">Editar Etiqueta / Nota</h3>
        </div>
        <button type="button" data-close-modal="modal-cell-note" class="glass-btn w-8 h-8 rounded-lg flex items-center justify-center text-xs cursor-pointer">✕</button>
      </div>
      <form id="form-cell-note" class="space-y-3">
        <input type="hidden" id="field-cell-id" />
        <div>
          <label class="block text-xs font-bold text-white/80 mb-1">Nota o etiqueta corta de la celda</label>
          <input id="field-cell-note-text" type="text" placeholder="Ej: Lección oral / Traer regla / Examen..." class="studio-input w-full px-3.5 py-2.5 rounded-xl text-xs" />
        </div>
        <div class="flex items-center justify-between pt-2">
          <button id="btn-clear-cell-note" type="button" class="glass-btn px-3 py-2 rounded-xl text-xs cursor-pointer">Quitar nota</button>
          <button type="submit" class="bg-[#00F5D4] text-[#070B10] font-extrabold px-4 py-2 rounded-xl text-xs cursor-pointer">Guardar</button>
        </div>
      </form>
    </div>
  </div>

  <!-- ==================== MODAL 5: DETALLE COMPLETO ==================== -->
  <div id="modal-detail" class="fixed inset-0 z-50 hidden items-center justify-center p-3 sm:p-5 bg-black/80 backdrop-blur-sm overflow-y-auto">
    <div class="liquid-panel rounded-2xl max-w-2xl w-full p-5 sm:p-6 space-y-4 my-auto fade-slide-in max-h-[92vh] overflow-y-auto">
      <div class="flex items-start justify-between gap-3">
        <div id="detail-tags" class="flex flex-wrap items-center gap-1.5"></div>
        <button type="button" data-close-modal="modal-detail" class="glass-btn w-8 h-8 rounded-lg flex items-center justify-center text-xs shrink-0 cursor-pointer">✕</button>
      </div>

      <div>
        <h3 id="detail-heading" class="font-display text-xl sm:text-2xl font-extrabold text-white"></h3>
        <p id="detail-sub" class="text-xs font-bold text-[#00F5D4] mt-1"></p>
      </div>

      <div id="detail-body" class="bg-black/45 border border-white/15 rounded-xl p-4 text-xs sm:text-sm text-white/90 leading-relaxed whitespace-pre-line"></div>

      <div id="detail-link-box" class="hidden">
        <a id="detail-link-anchor" href="#" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 px-4 py-2 rounded-xl bg-[#00B4D8]/25 border border-[#00B4D8] text-[#00F5D4] text-xs font-bold hover:bg-[#00B4D8]/40 transition-colors">
          <span>Abrir recurso / enlace adjunto</span>
          <span>↗</span>
        </a>
      </div>

      <div id="detail-materials-box" class="hidden space-y-1.5">
        <span class="text-[11px] font-tech uppercase tracking-wider text-[#00FF87]">Materiales:</span>
        <div id="detail-materials-list" class="flex flex-wrap gap-1.5"></div>
      </div>

      <div id="detail-photos-box" class="hidden space-y-2">
        <span class="text-[11px] font-tech uppercase tracking-wider text-white/70">Fotos Adjuntas (toca para ampliar):</span>
        <div id="detail-photos-grid" class="grid grid-cols-2 sm:grid-cols-3 gap-2.5"></div>
      </div>

      <div class="flex flex-wrap items-center justify-between gap-2 pt-3 border-t border-white/15">
        <div class="flex items-center gap-2">
          <button id="btn-detail-check" type="button" class="glass-btn px-4 py-2 rounded-xl text-xs font-bold cursor-pointer">
            Marcar completada
          </button>
          <button id="btn-detail-share" type="button" class="glass-btn px-4 py-2 rounded-xl text-xs font-bold text-[#00F5D4] cursor-pointer">
            Copiar WhatsApp
          </button>
        </div>
        <button type="button" data-close-modal="modal-detail" class="glass-btn px-4 py-2 rounded-xl text-xs font-bold cursor-pointer">Cerrar</button>
      </div>
    </div>
  </div>

  <!-- ==================== LIGHTBOX DE FOTOS ==================== -->
  <div id="modal-lightbox" class="fixed inset-0 z-[60] hidden items-center justify-center p-4 bg-black/90">
    <button type="button" data-close-modal="modal-lightbox" class="fixed top-4 right-4 glass-btn w-10 h-10 rounded-xl flex items-center justify-center text-sm font-bold cursor-pointer">✕</button>
    <img id="lightbox-image" src="" alt="Foto ampliada" class="max-w-full max-h-[88vh] rounded-xl border border-white/25 object-contain" />
  </div>

  <!-- ==================== TOASTS ==================== -->
  <div id="toast-box" class="fixed bottom-4 right-4 z-[70] flex flex-col gap-2 pointer-events-none"></div>

  <script>
    (function () {
      'use strict';

      /* ==================== CONSTANTES Y LLAVE ==================== */
      const EDITOR_KEY = '226611222010226611222010';
      const STORAGE = {
        TASKS: 'bgu1b_pro_tasks_v1',
        EVALS: 'bgu1b_pro_evals_v1',
        CELL_NOTES: 'bgu1b_pro_cell_notes_v1',
        WALLPAPER: 'bgu1b_pro_wallpaper_v1',
        GLASS: 'bgu1b_pro_glass_v1',
        BANNER: 'bgu1b_pro_banner_v1',
        COMPLETED: 'bgu1b_pro_completed_v1',
        VISITS_LOCAL: 'bgu1b_pro_visits_v1'
      };

      // Horario Matricial Oficial Exacto BGU 1B (Lunes a Viernes, Bloques 1 a 6 + Receso)
      const MATRIX_ROWS = [
        {
          id: 'h1',
          time: '1.- 7:10 - 7:55',
          cells: {
            Lunes: { id: 'lun-1', span: 2, subject: 'Inglés', teacher: 'Lcda. Alejandra Sabando', color: '#00B4D8', defaultEval: true },
            Martes: { id: 'mar-1', span: 2, subject: 'Lengua y Literatura', teacher: 'Lcdo. Javier Mendoza', color: '#FACC15', defaultEval: true },
            Miércoles: { id: 'mie-1', span: 1, subject: 'Lengua y Literatura', teacher: 'Lcdo. Javier Mendoza', color: '#FACC15', defaultEval: false },
            Jueves: { id: 'jue-1', span: 2, subject: 'Educación Física', teacher: 'Lcda. Paula Anchundia', color: '#2563EB', defaultEval: true },
            Viernes: { id: 'vie-1', span: 2, subject: 'Lengua y Literatura', teacher: 'Lcdo. Javier Mendoza', color: '#FACC15', defaultEval: false }
          }
        },
        {
          id: 'h2',
          time: '2.- 7:55 - 8:40',
          cells: {
            Lunes: 'skip',
            Martes: 'skip',
            Miércoles: { id: 'mie-2', span: 2, subject: 'Educación para la ciudadanía', teacher: 'Lcdo. Luis Delgado', color: '#991B1B', defaultEval: true },
            Jueves: 'skip',
            Viernes: 'skip'
          }
        },
        {
          id: 'h3',
          time: '3.- 8:40 - 9:25',
          cells: {
            Lunes: { id: 'lun-3', span: 1, subject: 'Matemática', teacher: 'Ing. Gema Briones', color: '#EF4444', defaultEval: false },
            Martes: { id: 'mar-3', span: 1, subject: 'Cívica', teacher: 'Lcda. Alejandra Sabando', color: '#B45309', defaultEval: true },
            Miércoles: 'skip',
            Jueves: { id: 'jue-3', span: 1, subject: 'Biología', teacher: 'Biol. Walther Baque', color: '#0284C7', defaultEval: false },
            Viernes: { id: 'vie-3', span: 1, subject: 'Física', teacher: 'Ing. Carmen Triviño', color: '#3B82F6', defaultEval: false }
          }
        },
        {
          id: 'recess',
          recess: true,
          time: '9:25 - 9:55',
          label: 'RECESO BGU'
        },
        {
          id: 'h4',
          time: '4.- 9:55 - 10:40',
          cells: {
            Lunes: { id: 'lun-4', span: 2, subject: 'Educación Cultural y Artística', teacher: 'Lcdo. Luis Delgado', color: '#34D399', defaultEval: true },
            Martes: { id: 'mar-4', span: 2, subject: 'Matemática', teacher: 'Ing. Gema Briones', color: '#EF4444', defaultEval: true },
            Miércoles: { id: 'mie-4', span: 2, subject: 'Emprendimiento y Gestión', teacher: 'Ing. Ana Holguín', color: '#FEF08A', defaultEval: true },
            Jueves: { id: 'jue-4', span: 1, subject: 'Inglés', teacher: 'Lcda. Alejandra Sabando', color: '#00B4D8', defaultEval: false },
            Viernes: { id: 'vie-4', span: 2, subject: 'Historia', teacher: 'Lcda. Aidee Velez', color: '#10B981', defaultEval: true }
          }
        },
        {
          id: 'h5',
          time: '5.- 10:40 - 11:25',
          cells: {
            Lunes: 'skip',
            Martes: 'skip',
            Miércoles: 'skip',
            Jueves: { id: 'jue-5', span: 1, subject: 'Química', teacher: 'Lcdo. Diego Macías', color: '#B45309', defaultEval: false },
            Viernes: 'skip'
          }
        },
        {
          id: 'h6',
          time: '6.- 11:25 - 12:10',
          cells: {
            Lunes: { id: 'lun-6', span: 1, subject: 'Química', teacher: 'Lcdo. Diego Macías', color: '#B45309', defaultEval: true },
            Martes: { id: 'mar-6', span: 1, subject: 'Biología', teacher: 'Biol. Walther Baque', color: '#0284C7', defaultEval: true },
            Miércoles: { id: 'mie-6', span: 1, subject: 'Física', teacher: 'Ing. Carmen Triviño', color: '#3B82F6', defaultEval: true },
            Jueves: { id: 'jue-6', span: 1, subject: 'Matemática', teacher: 'Ing. Gema Briones', color: '#EF4444', defaultEval: false },
            Viernes: { id: 'vie-6', span: 1, subject: 'Filosofía', teacher: 'Lcdo. Orlando Ortiz', color: '#DC2626', defaultEval: true }
          }
        }
      ];

      // Presets de Fondo: Celeste-Verde Neón, Verde Esmeralda, Azul Cobalto, Blanco Editorial, Negro Carbono
      const WALLPAPERS = [
        {
          id: 'celeste-verde',
          name: 'Celeste-Verde Neón',
          bg: 'radial-gradient(circle at 20% 20%, rgba(0, 245, 212, 0.36) 0%, transparent 48%), radial-gradient(circle at 82% 78%, rgba(0, 255, 135, 0.24) 0%, transparent 50%), linear-gradient(155deg, #070B10 0%, #091B1F 55%, #070B10 100%)'
        },
        {
          id: 'verde-esmeralda',
          name: 'Verde Esmeralda',
          bg: 'radial-gradient(circle at 25% 22%, rgba(0, 255, 135, 0.35) 0%, transparent 48%), radial-gradient(circle at 80% 75%, rgba(0, 245, 212, 0.22) 0%, transparent 50%), linear-gradient(160deg, #070B10 0%, #082118 100%)'
        },
        {
          id: 'azul-cobalto',
          name: 'Azul Cobalto',
          bg: 'radial-gradient(circle at 75% 20%, rgba(0, 180, 216, 0.44) 0%, transparent 50%), radial-gradient(circle at 22% 80%, rgba(0, 245, 212, 0.22) 0%, transparent 48%), linear-gradient(155deg, #070B10 0%, #0A2038 100%)'
        },
        {
          id: 'blanco-editorial',
          name: 'Blanco Editorial',
          bg: 'radial-gradient(circle at 18% 25%, rgba(0, 245, 212, 0.42) 0%, transparent 46%), radial-gradient(circle at 82% 30%, rgba(0, 180, 216, 0.38) 0%, transparent 46%), linear-gradient(135deg, #E8F5F2 0%, #FFFFFF 55%, #DCF0F7 100%)'
        },
        {
          id: 'negro-carbono',
          name: 'Negro Carbono',
          bg: 'radial-gradient(circle at 50% 10%, rgba(0, 245, 212, 0.16) 0%, transparent 45%), linear-gradient(180deg, #05070A 0%, #070B10 100%)'
        }
      ];

      const INITIAL_TASKS = [
        {
          id: 'pub-1',
          day: 'Lunes',
          subject: 'Inglés',
          teacher: 'Lcda. Alejandra Sabando',
          category: 'Evaluación / Aviso',
          priority: 'Fijada',
          date: '2026-11-30',
          title: 'Evaluación de Inglés: Present Perfect & Vocabulario',
          desc: 'Repasar estructura afirmativa, negativa e interrogativa y lista de verbos irregulares trabajada en clase.',
          materials: ['Esfero azul o negro', 'Cuaderno de Inglés'],
          link: '',
          photos: [],
          createdAt: Date.now() - 10000
        },
        {
          id: 'pub-2',
          day: 'Miércoles',
          subject: 'Emprendimiento y Gestión',
          teacher: 'Ing. Ana Holguín',
          category: 'Exposición',
          priority: 'Urgente',
          date: '2026-12-02',
          title: 'Exposición: Propuesta de Emprendimiento y Costos',
          desc: 'Exposición por equipos explicando segmento de clientes, propuesta de valor y cálculo de costos básicos.',
          materials: ['Material visual de apoyo', 'Hoja resumen por grupo'],
          link: '',
          photos: [],
          createdAt: Date.now() - 20000
        },
        {
          id: 'pub-3',
          day: 'Lunes',
          subject: 'Educación Cultural y Artística',
          teacher: 'Lcdo. Luis Delgado',
          category: 'Materiales',
          priority: 'Normal',
          date: '2026-11-30',
          title: 'Materiales para Práctica de Teoría del Color',
          desc: 'Traer los materiales completos para trabajar durante los bloques 4 y 5 del horario oficial.',
          materials: ['Cartulina A3', 'Pinturas o témperas', 'Pinceles', 'Regla y lápiz HB'],
          link: '',
          photos: [],
          createdAt: Date.now() - 30000
        },
        {
          id: 'pub-4',
          day: 'Martes',
          subject: 'Matemática',
          teacher: 'Ing. Gema Briones',
          category: 'Tarea',
          priority: 'Normal',
          date: '2026-12-01',
          title: 'Ejercicios de Ecuaciones y Funciones Lineales',
          desc: 'Resolver los ejercicios propuestos en clase mostrando procedimiento ordenado y comprobación.',
          materials: ['Cuaderno a cuadros', 'Regla'],
          link: '',
          photos: [],
          createdAt: Date.now() - 40000
        }
      ];

      /* ==================== ESTADO ==================== */
      const state = {
        isEditor: false,
        tasks: [],
        evalOverrides: {},
        cellNotes: {},
        completedIds: [],
        bannerText: '',
        filterDay: 'Todos',
        filterCat: 'Todas',
        search: '',
        formPhotos: [],
        activeDetailId: null,
        reelActive: true
      };

      /* ==================== INICIALIZACIÓN ==================== */
      function init() {
        loadState();
        initVisitors();
        applySavedWallpaper();
        applyGlassIntensity();
        renderWallpaperGrid();
        renderBanner();
        populateSubjectsForDay('Lunes');
        renderTasks();
        renderMatrixSchedule();
        startShowreelCanvas();
        bindEvents();
      }

      function loadState() {
        try {
          const t = localStorage.getItem(STORAGE.TASKS);
          state.tasks = t ? JSON.parse(t) : [...INITIAL_TASKS];
          if (!t) saveTasks();

          const ev = localStorage.getItem(STORAGE.EVALS);
          state.evalOverrides = ev ? JSON.parse(ev) : {};

          const cn = localStorage.getItem(STORAGE.CELL_NOTES);
          state.cellNotes = cn ? JSON.parse(cn) : {};

          const co = localStorage.getItem(STORAGE.COMPLETED);
          state.completedIds = co ? JSON.parse(co) : [];

          state.bannerText = localStorage.getItem(STORAGE.BANNER) || '';
        } catch (err) {
          state.tasks = [...INITIAL_TASKS];
        }
      }

      function saveTasks() {
        try {
          localStorage.setItem(STORAGE.TASKS, JSON.stringify(state.tasks));
        } catch (err) {
          showToast('Límite de almacenamiento alcanzado: reduce el número o tamaño de fotos.');
        }
      }

      /* ==================== CONTADOR DE VISITAS PERSISTENTE CON FALLBACK ==================== */
      async function initVisitors(increment = true) {
        const mainCounter = document.getElementById('live-visits-count');
        const reelBadge = document.getElementById('reel-visits-badge');

        let count = parseInt(localStorage.getItem(STORAGE.VISITS_LOCAL) || '1280', 10);
        if (Number.isNaN(count) || count < 0) count = 1280;

        if (increment) {
          count += 1;
          try {
            localStorage.setItem(STORAGE.VISITS_LOCAL, String(count));
          } catch (e) {}
        }

        const paint = (val) => {
          const text = Number(val).toLocaleString('es-EC');
          if (mainCounter) mainCounter.textContent = text;
          if (reelBadge) reelBadge.textContent = `VISITAS: ${text}`;
        };

        paint(count);

        // Intento de sincronización remota segura sin bloquear ni fallar si no hay red
        try {
          const controller = new AbortController();
          const timer = setTimeout(() => controller.abort(), 2500);
          const url = increment
            ? 'https://api.counterapi.dev/v1/1rob-bgu-1b-2026/visitas/up'
            : 'https://api.counterapi.dev/v1/1rob-bgu-1b-2026/visitas';
          const res = await fetch(url, { signal: controller.signal, cache: 'no-store' });
          clearTimeout(timer);
          if (res.ok) {
            const json = await res.json();
            if (json && typeof json.count === 'number') {
              const merged = Math.max(json.count + 1250, count);
              try { localStorage.setItem(STORAGE.VISITS_LOCAL, String(merged)); } catch (e) {}
              paint(merged);
            }
          }
        } catch (e) {
          // Fallback localStorage garantizado ya aplicado
        }
      }

      /* ==================== SHOWREEL CANVAS 2D 'WEBSITES IN 2026' (60FPS) ==================== */
      let reelRafId = null;
      let reelStartTime = 0;

      function startShowreelCanvas() {
        const canvas = document.getElementById('showreel-canvas');
        const sceneLabel = document.getElementById('reel-scene-label');
        if (!canvas) return;
        const ctx = canvas.getContext('2d', { alpha: false });

        const resizeCanvas = () => {
          const dpr = Math.min(window.devicePixelRatio || 1, 2);
          const w = window.innerWidth;
          const h = window.innerHeight;
          canvas.width = Math.floor(w * dpr);
          canvas.height = Math.floor(h * dpr);
          ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
        };

        resizeCanvas();
        window.addEventListener('resize', resizeCanvas, { passive: true });

        reelStartTime = performance.now();
        if (reelRafId) cancelAnimationFrame(reelRafId);

        const scenes = [
          'ESCENA 01 // RETÍCULA ARQUITECTÓNICA 2026',
          'ESCENA 02 // REFRACCIÓN PRISMÁTICA LIQUID GLASS',
          'ESCENA 03 // HORARIO MATRICIAL & TAREAS BGU 1B'
        ];

        const renderFrame = (now) => {
          if (!state.reelActive) return;
          const t = (now - reelStartTime) * 0.001;
          const w = window.innerWidth;
          const h = window.innerHeight;
          const cx = w * 0.5;
          const cy = h * 0.5;

          // Fondo profundo #070B10
          ctx.fillStyle = '#070B10';
          ctx.fillRect(0, 0, w, h);

          // Resplandor radial suave celeste-verde / azul eléctrico
          const grad = ctx.createRadialGradient(
            cx + Math.cos(t * 0.9) * (w * 0.14),
            cy + Math.sin(t * 0.7) * (h * 0.12),
            10,
            cx,
            cy,
            Math.max(w, h) * 0.62
          );
          grad.addColorStop(0, 'rgba(0, 245, 212, 0.22)');
          grad.addColorStop(0.45, 'rgba(0, 180, 216, 0.10)');
          grad.addColorStop(1, 'rgba(7, 11, 16, 0)');
          ctx.fillStyle = grad;
          ctx.fillRect(0, 0, w, h);

          // Líneas arquitectónicas finas de precisión en movimiento
          ctx.lineWidth = 1;
          const step = 72;
          const offsetX = (t * 28) % step;
          ctx.strokeStyle = 'rgba(255, 255, 255, 0.05)';
          for (let x = -step + offsetX; x < w + step; x += step) {
            ctx.beginPath();
            ctx.moveTo(x, 0);
            ctx.lineTo(x, h);
            ctx.stroke();
          }

          // Marco geométrico central tipo "Websites in 2026"
          const boxW = Math.min(w * 0.76, 540);
          const boxH = Math.min(h * 0.44, 320);
          const bx = cx - boxW * 0.5;
          const by = cy - boxH * 0.5;

          ctx.save();
          ctx.translate(cx, cy);
          ctx.rotate(Math.sin(t * 0.8) * 0.035);
          ctx.translate(-cx, -cy);

          // Separación cromática sutil en bordes del marco (cian-verde y azul)
          ctx.strokeStyle = 'rgba(0, 245, 212, 0.45)';
          ctx.strokeRect(bx - 3, by, boxW, boxH);

          ctx.strokeStyle = 'rgba(0, 180, 216, 0.45)';
          ctx.strokeRect(bx + 3, by, boxW, boxH);

          ctx.strokeStyle = 'rgba(255, 255, 255, 0.26)';
          ctx.strokeRect(bx, by, boxW, boxH);

          // Barra de luz que cruza el marco
          const sweepY = by + ((Math.sin(t * 1.4) + 1) * 0.5) * boxH;
          const barGrad = ctx.createLinearGradient(bx, sweepY, bx + boxW, sweepY);
          barGrad.addColorStop(0, 'rgba(0, 245, 212, 0)');
          barGrad.addColorStop(0.5, 'rgba(0, 255, 135, 0.55)');
          barGrad.addColorStop(1, 'rgba(0, 180, 216, 0)');
          ctx.fillStyle = barGrad;
          ctx.fillRect(bx, sweepY - 1, boxW, 2);

          // Anillo orbital de precisión
          const radius = Math.min(boxW, boxH) * 0.34;
          ctx.strokeStyle = 'rgba(0, 245, 212, 0.32)';
          ctx.beginPath();
          ctx.arc(cx, cy, radius, t * 0.7, t * 0.7 + Math.PI * 1.35);
          ctx.stroke();

          ctx.restore();

          // Actualizar etiqueta de escena cada ~3.2s
          const idx = Math.floor(t / 3.2) % scenes.length;
          if (sceneLabel && sceneLabel.textContent !== scenes[idx]) {
            sceneLabel.textContent = scenes[idx];
          }

          reelRafId = requestAnimationFrame(renderFrame);
        };

        reelRafId = requestAnimationFrame(renderFrame);
      }

      function enterPortalFromReel() {
        const reel = document.getElementById('intro-showreel');
        if (!reel) return;
        reel.classList.add('reel-exit');
        setTimeout(() => {
          reel.style.display = 'none';
          state.reelActive = false;
          if (reelRafId) cancelAnimationFrame(reelRafId);
        }, 360);
      }

      function openPortalReel() {
        const reel = document.getElementById('intro-showreel');
        if (!reel) return;
        reel.style.display = 'block';
        state.reelActive = true;
        requestAnimationFrame(() => {
          reel.classList.remove('reel-exit');
          startShowreelCanvas();
        });
      }

      /* ==================== FONDOS Y LIQUID GLASS ==================== */
      function applySavedWallpaper() {
        const el = document.getElementById('app-wallpaper');
        if (!el) return;
        try {
          const saved = localStorage.getItem(STORAGE.WALLPAPER);
          el.style.backgroundImage = saved
            ? (saved.startsWith('data:image') ? `url("${saved}")` : saved)
            : WALLPAPERS[0].bg;
        } catch (e) {
          el.style.backgroundImage = WALLPAPERS[0].bg;
        }
      }

      function setWallpaper(bgVal) {
        const el = document.getElementById('app-wallpaper');
        if (!el) return;
        el.style.backgroundImage = bgVal.startsWith('data:image') ? `url("${bgVal}")` : bgVal;
        try {
          localStorage.setItem(STORAGE.WALLPAPER, bgVal);
        } catch (e) {
          showToast('Fondo aplicado en sesión actual.');
        }
        showToast('Fondo actualizado en tiempo real');
      }

      function applyGlassIntensity() {
        let level = 1;
        try {
          level = parseInt(localStorage.getItem(STORAGE.GLASS) || '1', 10);
        } catch (e) {}
        const slider = document.getElementById('slider-glass-intensity');
        const label = document.getElementById('glass-intensity-val');
        if (slider) slider.value = String(level);

        const presets = [
          { name: 'Sutil (60fps)', alpha: '0.07', glow: '0.28', blur: '10px' },
          { name: 'Medio (60fps)', alpha: '0.14', glow: '0.50', blur: '14px' },
          { name: 'Intenso Prisma', alpha: '0.24', glow: '0.78', blur: '18px' }
        ];
        const p = presets[level] || presets[1];
        document.documentElement.style.setProperty('--glass-alpha', p.alpha);
        document.documentElement.style.setProperty('--glass-glow', p.glow);
        document.documentElement.style.setProperty('--glass-blur', p.blur);
        if (label) label.textContent = p.name;
      }

      function renderWallpaperGrid() {
        const grid = document.getElementById('presets-wallpaper-grid');
        if (!grid) return;
        grid.innerHTML = WALLPAPERS.map(wp => `
          <button type="button" data-wp-bg="${wp.bg}" class="relative h-20 rounded-xl overflow-hidden border border-white/25 hover:border-[#00F5D4] transition-all cursor-pointer">
            <div class="absolute inset-0" style="background-image: ${wp.bg}; background-size: cover;"></div>
            <span class="absolute inset-x-0 bottom-0 bg-black/65 py-1 px-2 text-[10px] font-bold text-white text-center">
              ${escapeHtml(wp.name)}
            </span>
          </button>
        `).join('');
      }

      /* ==================== AVISO GLOBAL ==================== */
      function renderBanner() {
        const banner = document.getElementById('pinned-banner');
        const txt = document.getElementById('pinned-banner-text');
        const editBtn = document.getElementById('btn-edit-banner-inline');
        if (!banner || !txt) return;

        if (state.bannerText && state.bannerText.trim().length > 0) {
          banner.classList.remove('hidden');
          txt.textContent = state.bannerText;
          if (editBtn) editBtn.classList.toggle('hidden', !state.isEditor);
        } else {
          banner.classList.add('hidden');
        }
      }

      /* ==================== MODO ESPECTADOR / MODO EDITOR ==================== */
      function setEditorMode(enabled) {
        state.isEditor = enabled;
        const badge = document.getElementById('badge-mode');
        const btnStudio = document.getElementById('btn-editor-studio');
        const btnNew = document.getElementById('btn-new-task');
        const iconLock = document.getElementById('icon-lock');
        const iconUnlock = document.getElementById('icon-unlock');
        const lblKey = document.getElementById('label-key-btn');

        if (enabled) {
          badge.textContent = 'Modo Editor Pro';
          badge.className = 'text-[10px] font-tech font-extrabold uppercase tracking-wider px-2 py-0.5 rounded-md bg-[#00FF87]/20 border border-[#00FF87] text-[#00FF87]';
          btnStudio.classList.remove('hidden');
          btnStudio.classList.add('flex');
          btnNew.classList.remove('hidden');
          btnNew.classList.add('flex');
          iconLock.classList.add('hidden');
          iconUnlock.classList.remove('hidden');
          lblKey.textContent = 'Bloquear';
          showToast('Modo Editor desbloqueado');
        } else {
          badge.textContent = 'Modo Espectador';
          badge.className = 'text-[10px] font-tech font-bold uppercase tracking-wider px-2 py-0.5 rounded-md bg-white/10 border border-white/20 text-[#00F5D4]';
          btnStudio.classList.add('hidden');
          btnStudio.classList.remove('flex');
          btnNew.classList.add('hidden');
          btnNew.classList.remove('flex');
          iconLock.classList.remove('hidden');
          iconUnlock.classList.add('hidden');
          lblKey.textContent = 'Llave Editor';
          showToast('Modo Espectador activo');
        }

        renderBanner();
        renderTasks();
        renderMatrixSchedule();
      }

      /* ==================== HORARIO MATRICIAL BGU 1B ==================== */
      function renderMatrixSchedule() {
        const tbody = document.getElementById('matrix-schedule-body');
        if (!tbody) return;
        const days = ['Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes'];

        tbody.innerHTML = MATRIX_ROWS.map(row => {
          if (row.recess) {
            return `
              <tr class="bg-white/10">
                <td class="p-2.5 text-center font-tech font-bold text-[#00F5D4] border-r border-white/20 whitespace-nowrap">
                  ${row.time}
                </td>
                <td colspan="5" class="p-2.5 text-center font-display font-extrabold tracking-[0.28em] text-white uppercase">
                  ${row.label}
                </td>
              </tr>
            `;
          }

          const tds = days.map(day => {
            const cell = row.cells[day];
            if (cell === 'skip') return '';

            const hasEval = state.evalOverrides.hasOwnProperty(cell.id)
              ? state.evalOverrides[cell.id]
              : cell.defaultEval;

            const note = state.cellNotes[cell.id] || '';
            const linkedCount = state.tasks.filter(t => t.day === day && t.subject === cell.subject).length;

            return `
              <td rowspan="${cell.span}" class="p-0 border-r border-white/20 align-top">
                <div class="h-full min-h-[78px] flex items-stretch hover:bg-white/[0.07] transition-colors">
                  <div class="w-3 sm:w-3.5 shrink-0" style="background-color: ${cell.color};"></div>
                  <div class="flex-1 p-2.5 flex flex-col justify-between gap-1.5">
                    <button type="button" data-cell-day="${day}" data-cell-subject="${escapeHtml(cell.subject)}" class="text-left w-full cursor-pointer">
                      <div class="font-bold text-white hover:text-[#00F5D4] leading-snug">
                        ${escapeHtml(cell.subject)} –
                      </div>
                      <div class="text-[11px] text-white/75 leading-tight mt-0.5">
                        ${escapeHtml(cell.teacher)}
                      </div>
                      ${note ? `
                        <div class="mt-1 px-2 py-0.5 rounded bg-[#00B4D8]/20 border border-[#00B4D8]/50 text-[10px] font-semibold text-[#00F5D4]">
                          ${escapeHtml(note)}
                        </div>
                      ` : ''}
                    </button>

                    <div class="flex flex-wrap items-center gap-1.5 mt-1">
                      ${hasEval ? `<span class="tag-evaluacion">Evaluación</span>` : ''}

                      ${linkedCount > 0 ? `
                        <button type="button" data-cell-day="${day}" data-cell-subject="${escapeHtml(cell.subject)}" class="px-2 py-0.5 rounded bg-[#00B4D8]/25 border border-[#00B4D8] text-[#00F5D4] font-tech font-bold text-[10px] cursor-pointer">
                          ${linkedCount} pub.
                        </button>
                      ` : ''}

                      ${state.isEditor ? `
                        <button type="button" data-toggle-eval="${cell.id}" class="px-1.5 py-0.5 rounded bg-white/10 hover:bg-white/25 text-[9px] font-tech text-white/85 cursor-pointer">
                          ${hasEval ? 'Sin Eval' : '+ Eval'}
                        </button>
                        <button type="button" data-edit-cell-note="${cell.id}" data-cell-label="${escapeHtml(cell.subject)} (${day})" class="px-1.5 py-0.5 rounded bg-white/10 hover:bg-white/25 text-[9px] font-tech text-[#00F5D4] cursor-pointer">
                          Nota
                        </button>
                        <button type="button" data-add-cell-day="${day}" data-add-cell-subject="${escapeHtml(cell.subject)}" class="px-1.5 py-0.5 rounded bg-[#00FF87]/20 hover:bg-[#00FF87]/40 text-[9px] font-tech font-bold text-[#00FF87] cursor-pointer">
                          + Publicar
                        </button>
                      ` : ''}
                    </div>
                  </div>
                </div>
              </td>
            `;
          }).join('');

          return `
            <tr>
              <td class="p-2.5 text-center font-tech font-bold text-white/90 border-r border-white/20 whitespace-nowrap bg-white/[0.03]">
                ${row.time}
              </td>
              ${tds}
            </tr>
          `;
        }).join('');
      }

      /* ==================== PUBLICACIONES (TAREA, EXPOSICIÓN, MATERIALES, EVALUACIÓN / AVISO) ==================== */
      function getPriorityBadge(prio) {
        if (prio === 'Urgente') return 'bg-rose-500/25 border-rose-400 text-rose-200';
        if (prio === 'Fijada') return 'bg-[#00FF87]/20 border-[#00FF87] text-[#00FF87]';
        return 'bg-white/10 border-white/20 text-white/75';
      }

      function renderTasks() {
        const container = document.getElementById('tasks-container');
        const empty = document.getElementById('tasks-empty-state');
        const badgeCount = document.getElementById('badge-tasks-count');
        const miniPubs = document.getElementById('stat-posts-mini');
        if (!container) return;

        // Ordenar: primero las marcadas como "Fijada" o "Urgente", luego por fecha de creación
        const sorted = [...state.tasks].sort((a, b) => {
          const rank = p => (p === 'Fijada' ? 0 : p === 'Urgente' ? 1 : 2);
          const diff = rank(a.priority) - rank(b.priority);
          if (diff !== 0) return diff;
          return (b.createdAt || 0) - (a.createdAt || 0);
        });

        const total = sorted.length;
        if (miniPubs) miniPubs.textContent = String(total);

        const doneCount = sorted.filter(t => state.completedIds.includes(t.id)).length;
        const pct = total > 0 ? Math.round((doneCount / total) * 100) : 0;
        document.getElementById('student-progress-bar').style.width = `${pct}%`;
        document.getElementById('student-progress-text').textContent = `${pct}%`;

        const filtered = sorted.filter(t => {
          const matchDay = state.filterDay === 'Todos' || t.day === state.filterDay;
          const matchCat = state.filterCat === 'Todas' || t.category === state.filterCat;
          const q = state.search.trim().toLowerCase();
          const matchQ = !q ||
            t.title.toLowerCase().includes(q) ||
            t.subject.toLowerCase().includes(q) ||
            t.teacher.toLowerCase().includes(q) ||
            t.desc.toLowerCase().includes(q);
          return matchDay && matchCat && matchQ;
        });

        badgeCount.textContent = String(filtered.length);

        if (filtered.length === 0) {
          container.innerHTML = '';
          empty.classList.remove('hidden');
          return;
        }

        empty.classList.add('hidden');

        container.innerHTML = filtered.map(task => {
          const isDone = state.completedIds.includes(task.id);
          const hasPhotos = Array.isArray(task.photos) && task.photos.length > 0;
          const hasMaterials = Array.isArray(task.materials) && task.materials.length > 0;

          return `
            <article class="liquid-card rounded-2xl p-4 sm:p-5 flex flex-col justify-between gap-3.5 fade-slide-in ${isDone ? 'opacity-65' : ''}">
              <div class="space-y-2.5">
                <div class="flex items-center justify-between gap-2">
                  <div class="flex flex-wrap items-center gap-1.5">
                    <span class="px-2.5 py-0.5 rounded-md bg-[#00F5D4] text-[#070B10] font-tech font-extrabold text-[10px] uppercase">
                      ${escapeHtml(task.category)}
                    </span>
                    <span class="px-2 py-0.5 rounded-md bg-white/10 border border-white/20 text-[10px] font-tech font-bold text-white">
                      ${escapeHtml(task.day)}
                    </span>
                    ${task.priority && task.priority !== 'Normal' ? `
                      <span class="px-2 py-0.5 rounded-md border text-[10px] font-tech font-bold ${getPriorityBadge(task.priority)}">
                        ${escapeHtml(task.priority)}
                      </span>
                    ` : ''}
                  </div>
                  <span class="text-[11px] font-tech text-white/65">${formatDate(task.date)}</span>
                </div>

                <div>
                  <div class="text-[11px] font-bold text-[#00F5D4]">
                    ${escapeHtml(task.subject)} <span class="text-white/60 font-normal">• ${escapeHtml(task.teacher)}</span>
                  </div>
                  <h3 class="font-display text-base sm:text-lg font-extrabold leading-snug mt-0.5 ${isDone ? 'line-through text-white/60' : 'text-white'}">
                    ${escapeHtml(task.title)}
                  </h3>
                </div>

                <p class="text-xs text-white/80 line-clamp-3 leading-relaxed">
                  ${escapeHtml(task.desc)}
                </p>

                ${hasMaterials ? `
                  <div class="flex flex-wrap gap-1 pt-0.5">
                    ${task.materials.slice(0, 3).map(m => `
                      <span class="px-2 py-0.5 rounded bg-[#00FF87]/15 border border-[#00FF87]/35 text-[#00FF87] text-[10px] font-medium">
                        • ${escapeHtml(m)}
                      </span>
                    `).join('')}
                    ${task.materials.length > 3 ? `<span class="text-[10px] text-white/60">+${task.materials.length - 3}</span>` : ''}
                  </div>
                ` : ''}

                ${hasPhotos ? `
                  <div class="flex items-center gap-2 pt-1">
                    ${task.photos.slice(0, 3).map((src, idx) => `
                      <button type="button" data-lightbox-task="${task.id}" data-lightbox-idx="${idx}" class="w-14 h-14 rounded-lg overflow-hidden border border-white/30 hover:border-[#00F5D4] shrink-0 cursor-pointer">
                        <img src="${src}" alt="Adjunto" class="w-full h-full object-cover" />
                      </button>
                    `).join('')}
                  </div>
                ` : ''}
              </div>

              <!-- Acciones -->
              <div class="flex items-center justify-between gap-2 pt-3 border-t border-white/10">
                <div class="flex items-center gap-1.5">
                  <button type="button" data-check-task="${task.id}" class="glass-btn px-2.5 py-1.5 rounded-lg text-[11px] font-bold cursor-pointer ${isDone ? 'bg-[#00FF87] text-[#070B10] border-[#00FF87]' : ''}">
                    ${isDone ? '✓ Lista' : 'Marcar'}
                  </button>
                  <button type="button" data-open-detail="${task.id}" class="glass-btn px-2.5 py-1.5 rounded-lg text-[11px] font-bold cursor-pointer">
                    Ver todo
                  </button>
                </div>

                <div class="flex items-center gap-1">
                  <button type="button" data-share-task="${task.id}" title="Copiar resumen para WhatsApp" class="glass-btn px-2 py-1.5 rounded-lg text-[10px] font-bold text-[#00F5D4] cursor-pointer">
                    WA
                  </button>

                  ${state.isEditor ? `
                    <button type="button" data-pin-task="${task.id}" title="Fijar / Desfijar" class="glass-btn px-2 py-1.5 rounded-lg text-[10px] font-bold text-[#00FF87] cursor-pointer">
                      ${task.priority === 'Fijada' ? '★' : '☆'}
                    </button>
                    <button type="button" data-dup-task="${task.id}" title="Duplicar" class="glass-btn px-2 py-1.5 rounded-lg text-[10px] font-bold text-white cursor-pointer">
                      Dup
                    </button>
                    <button type="button" data-edit-task="${task.id}" title="Editar" class="glass-btn px-2 py-1.5 rounded-lg text-[10px] font-bold text-[#00F5D4] cursor-pointer">
                      Edit
                    </button>
                    <button type="button" data-del-task="${task.id}" title="Borrar" class="glass-btn px-2 py-1.5 rounded-lg text-[10px] font-bold text-rose-400 cursor-pointer">
                      ✕
                    </button>
                  ` : ''}
                </div>
              </div>
            </article>
          `;
        }).join('');
      }

      /* ==================== MATERIAS POR DÍA ==================== */
      function getSubjectsForDay(day) {
        const out = [];
        const seen = new Set();
        MATRIX_ROWS.forEach(r => {
          if (r.recess) return;
          const cell = r.cells[day];
          if (cell && cell !== 'skip') {
            const key = `${cell.subject}||${cell.teacher}`;
            if (!seen.has(key)) {
              seen.add(key);
              out.push({ subject: cell.subject, teacher: cell.teacher });
            }
          }
        });
        return out;
      }

      function populateSubjectsForDay(day, preselect = null) {
        const sel = document.getElementById('field-task-subject');
        if (!sel) return;
        const list = getSubjectsForDay(day);
        sel.innerHTML = list.map(item => `
          <option value="${escapeHtml(item.subject)}||${escapeHtml(item.teacher)}" ${preselect === item.subject ? 'selected' : ''}>
            ${escapeHtml(item.subject)} — ${escapeHtml(item.teacher)}
          </option>
        `).join('');
      }

      /* ==================== COMPRESIÓN DE FOTOS EN CLIENTE ==================== */
      function compressImage(file) {
        return new Promise((resolve, reject) => {
          const reader = new FileReader();
          reader.onload = ev => {
            const img = new Image();
            img.onload = () => {
              const canvas = document.createElement('canvas');
              const maxSide = 880;
              let w = img.width;
              let h = img.height;
              if (w > maxSide || h > maxSide) {
                if (w >= h) {
                  h = Math.round((h * maxSide) / w);
                  w = maxSide;
                } else {
                  w = Math.round((w * maxSide) / h);
                  h = maxSide;
                }
              }
              canvas.width = w;
              canvas.height = h;
              canvas.getContext('2d').drawImage(img, 0, 0, w, h);
              resolve(canvas.toDataURL('image/jpeg', 0.75));
            };
            img.onerror = reject;
            img.src = ev.target.result;
          };
          reader.onerror = reject;
          reader.readAsDataURL(file);
        });
      }

      function renderFormPhotos() {
        const box = document.getElementById('preview-form-photos');
        if (!box) return;
        box.innerHTML = state.formPhotos.map((src, idx) => `
          <div class="relative aspect-square rounded-xl overflow-hidden border border-white/30">
            <img src="${src}" class="w-full h-full object-cover" />
            <button type="button" data-rm-photo="${idx}" class="absolute top-1 right-1 w-5 h-5 rounded-md bg-rose-600 text-white text-[10px] font-bold flex items-center justify-center cursor-pointer">✕</button>
          </div>
        `).join('');
      }

      /* ==================== MODALES Y DETALLE ==================== */
      function openModal(id) {
        const el = document.getElementById(id);
        if (!el) return;
        el.classList.remove('hidden');
        el.classList.add('flex');
      }

      function closeModal(id) {
        const el = document.getElementById(id);
        if (!el) return;
        el.classList.add('hidden');
        el.classList.remove('flex');
      }

      function openTaskModal(day = 'Lunes', subject = null, editObj = null) {
        document.getElementById('modal-task-heading').textContent = editObj ? 'Editar Publicación' : 'Nueva Publicación';
        document.getElementById('field-task-id').value = editObj ? editObj.id : '';
        document.getElementById('field-task-day').value = editObj ? editObj.day : day;
        populateSubjectsForDay(editObj ? editObj.day : day, editObj ? editObj.subject : subject);
        document.getElementById('field-task-cat').value = editObj ? editObj.category : 'Tarea';
        document.getElementById('field-task-priority').value = editObj ? (editObj.priority || 'Normal') : 'Normal';
        document.getElementById('field-task-date').value = editObj ? editObj.date : new Date().toISOString().split('T')[0];
        document.getElementById('field-task-title').value = editObj ? editObj.title : '';
        document.getElementById('field-task-desc').value = editObj ? editObj.desc : '';
        document.getElementById('field-task-materials').value = (editObj && editObj.materials) ? editObj.materials.join(', ') : '';
        document.getElementById('field-task-link').value = (editObj && editObj.link) ? editObj.link : '';
        state.formPhotos = (editObj && Array.isArray(editObj.photos)) ? [...editObj.photos] : [];
        renderFormPhotos();
        openModal('modal-task');
      }

      function openDetailModal(id) {
        const t = state.tasks.find(x => x.id === id);
        if (!t) return;
        state.activeDetailId = id;

        document.getElementById('detail-tags').innerHTML = `
          <span class="px-2.5 py-0.5 rounded-md bg-[#00F5D4] text-[#070B10] font-tech font-extrabold text-xs uppercase">${escapeHtml(t.category)}</span>
          <span class="px-2.5 py-0.5 rounded-md bg-white/10 border border-white/20 text-xs font-tech font-bold">${escapeHtml(t.day)}</span>
          <span class="px-2.5 py-0.5 rounded-md bg-white/10 text-xs font-tech text-white/75">${formatDate(t.date)}</span>
        `;
        document.getElementById('detail-heading').textContent = t.title;
        document.getElementById('detail-sub').textContent = `${t.subject} • ${t.teacher}`;
        document.getElementById('detail-body').textContent = t.desc;

        const linkBox = document.getElementById('detail-link-box');
        const linkAnchor = document.getElementById('detail-link-anchor');
        if (t.link && /^https?:\/\//i.test(t.link)) {
          linkBox.classList.remove('hidden');
          linkAnchor.href = t.link;
        } else {
          linkBox.classList.add('hidden');
        }

        const matBox = document.getElementById('detail-materials-box');
        const matList = document.getElementById('detail-materials-list');
        if (t.materials && t.materials.length > 0) {
          matBox.classList.remove('hidden');
          matList.innerHTML = t.materials.map(m => `
            <span class="px-2.5 py-1 rounded-lg bg-[#00FF87]/15 border border-[#00FF87]/40 text-[#00FF87] text-xs font-semibold">• ${escapeHtml(m)}</span>
          `).join('');
        } else {
          matBox.classList.add('hidden');
        }

        const photoBox = document.getElementById('detail-photos-box');
        const photoGrid = document.getElementById('detail-photos-grid');
        if (t.photos && t.photos.length > 0) {
          photoBox.classList.remove('hidden');
          photoGrid.innerHTML = t.photos.map((src, i) => `
            <button type="button" data-lightbox-task="${t.id}" data-lightbox-idx="${i}" class="aspect-video rounded-xl overflow-hidden border border-white/25 hover:border-[#00F5D4] cursor-pointer">
              <img src="${src}" class="w-full h-full object-cover" />
            </button>
          `).join('');
        } else {
          photoBox.classList.add('hidden');
        }

        const done = state.completedIds.includes(id);
        const btnCheck = document.getElementById('btn-detail-check');
        btnCheck.textContent = done ? '✓ Completada' : 'Marcar completada';
        btnCheck.className = `glass-btn px-4 py-2 rounded-xl text-xs font-bold cursor-pointer ${done ? 'bg-[#00FF87] text-[#070B10] border-[#00FF87]' : ''}`;

        openModal('modal-detail');
      }

      /* ==================== WHATSAPP & PORTAPAPELES ==================== */
      function copyClipboard(text) {
        const ta = document.createElement('textarea');
        ta.value = text;
        ta.style.position = 'fixed';
        ta.style.opacity = '0';
        document.body.appendChild(ta);
        ta.select();
        try {
          document.execCommand('copy');
          showToast('Copiado al portapapeles para WhatsApp');
        } catch (e) {
          showToast('No se pudo copiar en este dispositivo.');
        }
        document.body.removeChild(ta);
      }

      function shareTask(id) {
        const t = state.tasks.find(x => x.id === id);
        if (!t) return;
        const mats = (t.materials && t.materials.length) ? `\n📦 *Materiales:* ${t.materials.join(', ')}` : '';
        const link = t.link ? `\n🔗 *Enlace:* ${t.link}` : '';
        const msg = `📌 *1RO B. BGU (BGU 1B) - ${t.category.toUpperCase()}*\n🗓 *Día:* ${t.day} (${formatDate(t.date)})\n📘 *Materia:* ${t.subject} (${t.teacher})\n📝 *Título:* ${t.title}\nℹ️ *Detalle:* ${t.desc}${mats}${link}`;
        copyClipboard(msg);
      }

      /* ==================== EVENTOS ==================== */
      function bindEvents() {
        // Showreel 2026
        document.getElementById('btn-enter-portal').addEventListener('click', enterPortalFromReel);
        document.getElementById('btn-skip-reel').addEventListener('click', enterPortalFromReel);
        document.getElementById('btn-open-reel').addEventListener('click', openPortalReel);
        document.getElementById('btn-replay-reel').addEventListener('click', () => {
          reelStartTime = performance.now();
          showToast('Reiniciando secuencia 2026');
        });

        // Visitas
        document.getElementById('btn-refresh-visits').addEventListener('click', () => {
          initVisitors(true);
          showToast('Contador actualizado');
        });

        // Llave Editor
        document.getElementById('btn-key-modal').addEventListener('click', () => {
          if (state.isEditor) {
            setEditorMode(false);
          } else {
            document.getElementById('input-key-code').value = '';
            document.getElementById('error-key-code').classList.add('hidden');
            openModal('modal-key');
            setTimeout(() => document.getElementById('input-key-code').focus(), 80);
          }
        });

        document.getElementById('form-key').addEventListener('submit', e => {
          e.preventDefault();
          const code = document.getElementById('input-key-code').value.trim();
          if (code === EDITOR_KEY) {
            closeModal('modal-key');
            setEditorMode(true);
          } else {
            document.getElementById('error-key-code').classList.remove('hidden');
            document.getElementById('input-key-code').value = '';
          }
        });

        // Vistas Publicaciones vs Horario
        document.querySelectorAll('.nav-view-btn').forEach(btn => {
          btn.addEventListener('click', () => {
            document.querySelectorAll('.nav-view-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            const v = btn.getAttribute('data-view');
            document.getElementById('section-tareas').classList.toggle('hidden', v !== 'tareas');
            document.getElementById('section-horario').classList.toggle('hidden', v !== 'horario');
          });
        });

        // Filtros
        document.querySelectorAll('.filter-day-btn').forEach(btn => {
          btn.addEventListener('click', () => {
            document.querySelectorAll('.filter-day-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            state.filterDay = btn.getAttribute('data-filter-day');
            renderTasks();
          });
        });

        document.querySelectorAll('.filter-cat-btn').forEach(btn => {
          btn.addEventListener('click', () => {
            document.querySelectorAll('.filter-cat-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            state.filterCat = btn.getAttribute('data-filter-cat');
            renderTasks();
          });
        });

        document.getElementById('input-search').addEventListener('input', e => {
          state.search = e.target.value;
          renderTasks();
        });

        document.getElementById('btn-clear-filters').addEventListener('click', () => {
          state.filterDay = 'Todos';
          state.filterCat = 'Todas';
          state.search = '';
          document.getElementById('input-search').value = '';
          document.querySelectorAll('.filter-day-btn').forEach(b => b.classList.toggle('active', b.getAttribute('data-filter-day') === 'Todos'));
          document.querySelectorAll('.filter-cat-btn').forEach(b => b.classList.toggle('active', b.getAttribute('data-filter-cat') === 'Todas'));
          renderTasks();
          showToast('Filtros restablecidos');
        });

        // Botones Editor Pro
        document.getElementById('btn-new-task').addEventListener('click', () => openTaskModal('Lunes'));
        document.getElementById('btn-editor-studio').addEventListener('click', () => {
          document.getElementById('input-banner-msg').value = state.bannerText;
          openModal('modal-editor-studio');
        });
        document.getElementById('btn-edit-banner-inline').addEventListener('click', () => {
          document.getElementById('input-banner-msg').value = state.bannerText;
          openModal('modal-editor-studio');
        });
        document.getElementById('btn-lock-from-studio').addEventListener('click', () => {
          closeModal('modal-editor-studio');
          setEditorMode(false);
        });

        // Banner
        document.getElementById('btn-save-banner').addEventListener('click', () => {
          state.bannerText = document.getElementById('input-banner-msg').value.trim();
          try { localStorage.setItem(STORAGE.BANNER, state.bannerText); } catch (e) {}
          renderBanner();
          showToast('Aviso global guardado');
        });

        document.getElementById('btn-clear-banner').addEventListener('click', () => {
          state.bannerText = '';
          try { localStorage.removeItem(STORAGE.BANNER); } catch (e) {}
          document.getElementById('input-banner-msg').value = '';
          renderBanner();
          showToast('Aviso eliminado');
        });

        // Intensidad Liquid Glass
        document.getElementById('slider-glass-intensity').addEventListener('input', e => {
          try { localStorage.setItem(STORAGE.GLASS, e.target.value); } catch (err) {}
          applyGlassIntensity();
        });

        // Subir fondo personalizado
        document.getElementById('input-custom-wallpaper').addEventListener('change', async e => {
          const file = e.target.files[0];
          if (!file) return;
          try {
            const compressed = await compressImage(file);
            setWallpaper(compressed);
          } catch (err) {
            showToast('No se pudo cargar la imagen de fondo.');
          }
          e.target.value = '';
        });

        // Resumen WhatsApp y Respaldo JSON (Exportar / Importar)
        document.getElementById('btn-copy-whatsapp-summary').addEventListener('click', () => {
          if (state.tasks.length === 0) {
            showToast('No hay publicaciones para resumir.');
            return;
          }
          const lines = state.tasks.map((t, i) => `${i + 1}. *[${t.day} • ${t.category}]* ${t.subject}: ${t.title} (${formatDate(t.date)})`);
          copyClipboard(`📚 *RESUMEN 1RO B. BGU (BGU 1B)*\nTutora: Lcda. Alejandra Sabando Ponce\n\n${lines.join('\n')}`);
        });

        document.getElementById('btn-export-json').addEventListener('click', () => {
          const payload = {
            course: '1ro B. BGU',
            tutor: 'Lcda. Alejandra Sabando Ponce',
            exportedAt: new Date().toISOString(),
            bannerText: state.bannerText,
            tasks: state.tasks,
            evalOverrides: state.evalOverrides,
            cellNotes: state.cellNotes
          };
          const blob = new Blob([JSON.stringify(payload, null, 2)], { type: 'application/json' });
          const url = URL.createObjectURL(blob);
          const a = document.createElement('a');
          a.href = url;
          a.download = `respaldo-1roB-BGU-${new Date().toISOString().slice(0, 10)}.json`;
          a.click();
          URL.revokeObjectURL(url);
          showToast('Respaldo JSON exportado');
        });

        document.getElementById('input-import-json').addEventListener('change', e => {
          const file = e.target.files[0];
          if (!file) return;
          const reader = new FileReader();
          reader.onload = ev => {
            try {
              const data = JSON.parse(ev.target.result);
              if (Array.isArray(data.tasks)) {
                state.tasks = data.tasks;
                saveTasks();
              }
              if (typeof data.bannerText === 'string') {
                state.bannerText = data.bannerText;
                localStorage.setItem(STORAGE.BANNER, state.bannerText);
              }
              if (data.evalOverrides && typeof data.evalOverrides === 'object') {
                state.evalOverrides = data.evalOverrides;
                localStorage.setItem(STORAGE.EVALS, JSON.stringify(state.evalOverrides));
              }
              if (data.cellNotes && typeof data.cellNotes === 'object') {
                state.cellNotes = data.cellNotes;
                localStorage.setItem(STORAGE.CELL_NOTES, JSON.stringify(state.cellNotes));
              }
              renderBanner();
              renderTasks();
              renderMatrixSchedule();
              showToast('Respaldo JSON importado correctamente');
            } catch (err) {
              showToast('Archivo JSON no válido.');
            }
          };
          reader.readAsText(file);
          e.target.value = '';
        });

        // Formulario Publicación
        document.getElementById('field-task-day').addEventListener('change', e => {
          populateSubjectsForDay(e.target.value);
        });

        document.getElementById('field-task-photos').addEventListener('change', async e => {
          const files = Array.from(e.target.files || []);
          for (const f of files) {
            try {
              const compressed = await compressImage(f);
              state.formPhotos.push(compressed);
            } catch (err) {}
          }
          renderFormPhotos();
          e.target.value = '';
        });

        document.getElementById('form-task').addEventListener('submit', e => {
          e.preventDefault();
          const id = document.getElementById('field-task-id').value;
          const day = document.getElementById('field-task-day').value;
          const [subject, teacher] = document.getElementById('field-task-subject').value.split('||');
          const category = document.getElementById('field-task-cat').value;
          const priority = document.getElementById('field-task-priority').value;
          const date = document.getElementById('field-task-date').value;
          const title = document.getElementById('field-task-title').value.trim();
          const desc = document.getElementById('field-task-desc').value.trim();
          const rawMats = document.getElementById('field-task-materials').value.trim();
          const materials = rawMats ? rawMats.split(',').map(s => s.trim()).filter(Boolean) : [];
          const link = document.getElementById('field-task-link').value.trim();

          if (id) {
            const idx = state.tasks.findIndex(t => t.id === id);
            if (idx !== -1) {
              state.tasks[idx] = {
                ...state.tasks[idx],
                day, subject, teacher, category, priority, date, title, desc, materials, link,
                photos: [...state.formPhotos]
              };
            }
            showToast('Publicación actualizada');
          } else {
            state.tasks.unshift({
              id: 'pub-' + Date.now(),
              day, subject, teacher, category, priority, date, title, desc, materials, link,
              photos: [...state.formPhotos],
              createdAt: Date.now()
            });
            showToast('Publicación creada');
          }

          saveTasks();
          renderTasks();
          renderMatrixSchedule();
          closeModal('modal-task');
        });

        // Formulario Nota de Celda del Horario
        document.getElementById('form-cell-note').addEventListener('submit', e => {
          e.preventDefault();
          const cid = document.getElementById('field-cell-id').value;
          const txt = document.getElementById('field-cell-note-text').value.trim();
          if (txt) state.cellNotes[cid] = txt;
          else delete state.cellNotes[cid];
          try { localStorage.setItem(STORAGE.CELL_NOTES, JSON.stringify(state.cellNotes)); } catch (err) {}
          renderMatrixSchedule();
          closeModal('modal-cell-note');
          showToast('Nota del horario guardada');
        });

        document.getElementById('btn-clear-cell-note').addEventListener('click', () => {
          const cid = document.getElementById('field-cell-id').value;
          delete state.cellNotes[cid];
          try { localStorage.setItem(STORAGE.CELL_NOTES, JSON.stringify(state.cellNotes)); } catch (err) {}
          renderMatrixSchedule();
          closeModal('modal-cell-note');
          showToast('Nota removida');
        });

        // Delegación global de clics
        document.addEventListener('click', e => {
          const closeBtn = e.target.closest('[data-close-modal]');
          if (closeBtn) {
            closeModal(closeBtn.getAttribute('data-close-modal'));
            return;
          }

          const wpBtn = e.target.closest('[data-wp-bg]');
          if (wpBtn) {
            setWallpaper(wpBtn.getAttribute('data-wp-bg'));
            return;
          }

          const rmPhoto = e.target.closest('[data-rm-photo]');
          if (rmPhoto) {
            state.formPhotos.splice(parseInt(rmPhoto.getAttribute('data-rm-photo'), 10), 1);
            renderFormPhotos();
            return;
          }

          const checkBtn = e.target.closest('[data-check-task]');
          if (checkBtn) {
            toggleDone(checkBtn.getAttribute('data-check-task'));
            return;
          }

          const detailBtn = e.target.closest('[data-open-detail]');
          if (detailBtn) {
            openDetailModal(detailBtn.getAttribute('data-open-detail'));
            return;
          }

          const shareBtn = e.target.closest('[data-share-task]');
          if (shareBtn) {
            shareTask(shareBtn.getAttribute('data-share-task'));
            return;
          }

          const pinBtn = e.target.closest('[data-pin-task]');
          if (pinBtn && state.isEditor) {
            const t = state.tasks.find(x => x.id === pinBtn.getAttribute('data-pin-task'));
            if (t) {
              t.priority = t.priority === 'Fijada' ? 'Normal' : 'Fijada';
              saveTasks();
              renderTasks();
              showToast(t.priority === 'Fijada' ? 'Publicación fijada arriba' : 'Publicación desfijada');
            }
            return;
          }

          const dupBtn = e.target.closest('[data-dup-task]');
          if (dupBtn && state.isEditor) {
            const t = state.tasks.find(x => x.id === dupBtn.getAttribute('data-dup-task'));
            if (t) {
              state.tasks.unshift({
                ...t,
                id: 'pub-' + Date.now(),
                title: t.title + ' (Copia)',
                createdAt: Date.now()
              });
              saveTasks();
              renderTasks();
              renderMatrixSchedule();
              showToast('Publicación duplicada');
            }
            return;
          }

          const editBtn = e.target.closest('[data-edit-task]');
          if (editBtn && state.isEditor) {
            const t = state.tasks.find(x => x.id === editBtn.getAttribute('data-edit-task'));
            if (t) openTaskModal(t.day, t.subject, t);
            return;
          }

          const delBtn = e.target.closest('[data-del-task]');
          if (delBtn && state.isEditor) {
            const id = delBtn.getAttribute('data-del-task');
            state.tasks = state.tasks.filter(x => x.id !== id);
            saveTasks();
            renderTasks();
            renderMatrixSchedule();
            showToast('Publicación eliminada');
            return;
          }

          const lbBtn = e.target.closest('[data-lightbox-task]');
          if (lbBtn) {
            const t = state.tasks.find(x => x.id === lbBtn.getAttribute('data-lightbox-task'));
            const idx = parseInt(lbBtn.getAttribute('data-lightbox-idx'), 10);
            if (t && t.photos && t.photos[idx]) {
              document.getElementById('lightbox-image').src = t.photos[idx];
              openModal('modal-lightbox');
            }
            return;
          }

          // Alternar Evaluación en celda del horario (Editor)
          const evalBtn = e.target.closest('[data-toggle-eval]');
          if (evalBtn && state.isEditor) {
            const cid = evalBtn.getAttribute('data-toggle-eval');
            let cur = false;
            MATRIX_ROWS.forEach(r => {
              if (r.cells) {
                Object.values(r.cells).forEach(c => {
                  if (c && c !== 'skip' && c.id === cid) {
                    cur = state.evalOverrides.hasOwnProperty(cid) ? state.evalOverrides[cid] : c.defaultEval;
                  }
                });
              }
            });
            state.evalOverrides[cid] = !cur;
            try { localStorage.setItem(STORAGE.EVALS, JSON.stringify(state.evalOverrides)); } catch (err) {}
            renderMatrixSchedule();
            showToast('Etiqueta Evaluación actualizada');
            return;
          }

          // Editar nota de celda del horario (Editor)
          const noteBtn = e.target.closest('[data-edit-cell-note]');
          if (noteBtn && state.isEditor) {
            const cid = noteBtn.getAttribute('data-edit-cell-note');
            document.getElementById('field-cell-id').value = cid;
            document.getElementById('cell-note-title').textContent = noteBtn.getAttribute('data-cell-label') || 'Nota de Celda';
            document.getElementById('field-cell-note-text').value = state.cellNotes[cid] || '';
            openModal('modal-cell-note');
            return;
          }

          // Crear publicación directa desde celda del horario (Editor)
          const addCellBtn = e.target.closest('[data-add-cell-day]');
          if (addCellBtn && state.isEditor) {
            openTaskModal(addCellBtn.getAttribute('data-add-cell-day'), addCellBtn.getAttribute('data-add-cell-subject'));
            return;
          }

          // Filtrar por materia/día al tocar una celda del horario
          const cellFilterBtn = e.target.closest('[data-cell-day]');
          if (cellFilterBtn) {
            const d = cellFilterBtn.getAttribute('data-cell-day');
            const s = cellFilterBtn.getAttribute('data-cell-subject');
            state.filterDay = d;
            state.search = s;
            document.getElementById('input-search').value = s;
            document.querySelectorAll('.filter-day-btn').forEach(b => {
              b.classList.toggle('active', b.getAttribute('data-filter-day') === d);
            });
            document.querySelector('[data-view="tareas"]').click();
            renderTasks();
            showToast(`${s} • ${d}`);
          }
        });

        document.getElementById('btn-detail-check').addEventListener('click', () => {
          if (!state.activeDetailId) return;
          toggleDone(state.activeDetailId);
          openDetailModal(state.activeDetailId);
        });

        document.getElementById('btn-detail-share').addEventListener('click', () => {
          if (state.activeDetailId) shareTask(state.activeDetailId);
        });
      }

      function toggleDone(id) {
        const idx = state.completedIds.indexOf(id);
        if (idx === -1) state.completedIds.push(id);
        else state.completedIds.splice(idx, 1);
        try { localStorage.setItem(STORAGE.COMPLETED, JSON.stringify(state.completedIds)); } catch (e) {}
        renderTasks();
      }

      function showToast(msg) {
        const box = document.getElementById('toast-box');
        if (!box) return;
        const el = document.createElement('div');
        el.className = 'liquid-panel px-4 py-2.5 rounded-xl text-xs font-bold text-white border-l-4 border-l-[#00F5D4] fade-slide-in';
        el.textContent = msg;
        box.appendChild(el);
        setTimeout(() => {
          el.style.opacity = '0';
          setTimeout(() => el.remove(), 220);
        }, 2600);
      }

      function formatDate(iso) {
        if (!iso) return '';
        const p = iso.split('-');
        return p.length === 3 ? `${p[2]}/${p[1]}/${p[0]}` : iso;
      }

      function escapeHtml(str) {
        if (str == null) return '';
        return String(str)
          .replace(/&/g, '&amp;')
          .replace(/</g, '&lt;')
          .replace(/>/g, '&gt;')
          .replace(/"/g, '&quot;');
      }

      window.addEventListener('DOMContentLoaded', init);
    })();
  </script>
</body>
</html>
```
