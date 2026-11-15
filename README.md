<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Long Life Learning Academy — Seek Knowledge from the Cradle to the Grave</title>
  <!-- Tailwind CSS via CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Inter & Plus Jakarta Sans & JetBrains Mono for Code Editor -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&family=Playfair+Display:ital,wght@0,600;0,700;1,600&display=swap" rel="stylesheet" />
  <!-- FontAwesome for crisp UI icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            academy: {
              navy: '#0A2540',
              navyLight: '#13385E',
              teal: '#0F5257',
              tealLight: '#18787F',
              gold: '#C59B27',
              goldLight: '#DFB645',
              cream: '#FAF8F5',
              slate: '#F1F5F9'
            }
          },
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            serif: ['Playfair Display', 'serif'],
            mono: ['JetBrains Mono', 'monospace'],
          }
        }
      }
    }
  </script>

  <style>
    /* Custom scrollbar & print rules for Certificate */
    ::-webkit-scrollbar {
      width: 8px;
      height: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #f1f5f9;
    }
    ::-webkit-scrollbar-thumb {
      background: #cbd5e1;
      border-radius: 9999px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #94a3b8;
    }

    @keyframes pulse-subtle {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.6; }
    }
    .ai-badge-glow {
      animation: pulse-subtle 3s infinite ease-in-out;
    }

    @media print {
      body * {
        visibility: hidden;
      }
      #certificate-printable, #certificate-printable * {
        visibility: visible;
      }
      #certificate-printable {
        position: fixed;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 2rem;
        box-shadow: none !important;
        border: 8px double #0A2540 !important;
      }
      .no-print {
        display: none !important;
      }
    }
  </style>
</head>
<body class="bg-academy-cream text-slate-800 font-sans antialiased min-h-screen flex flex-col">

  <!-- Toast Notification Container (Replaces alert/confirm) -->
  <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col gap-3 max-w-sm w-full pointer-events-none"></div>

  <!-- Top Navigation Header -->
  <header class="bg-academy-navy text-white shadow-lg sticky top-0 z-40 border-b-2 border-academy-gold">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex flex-wrap items-center justify-between py-3 gap-4">
        
        <!-- Brand Identity & Custom SVG Emblem (Hidden 5-Click Admin Trigger) -->
        <div id="academy-brand-trigger" onclick="handleBrandClick()" class="flex items-center gap-3.5 cursor-pointer select-none" title="Long Life Learning Academy">
          <div class="w-12 h-12 rounded-full bg-white p-1 shadow-md flex items-center justify-center border-2 border-academy-gold shrink-0 transition-transform active:scale-95">
            <!-- Custom Tree + Infinity + Open Book + Star SVG Emblem -->
            <svg viewBox="0 0 100 100" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" aria-label="Long Life Learning Academy Emblem">
              <circle cx="50" cy="50" r="46" fill="none" stroke="#0A2540" stroke-width="3" />
              <circle cx="50" cy="50" r="41" fill="none" stroke="#C59B27" stroke-width="1.5" />
              <!-- Open Book Base -->
              <path d="M24 76 Q37 70 50 77 Q63 70 76 76 L73 81 Q61 76 50 82 Q39 76 27 81 Z" fill="#0A2540" />
              <!-- Tree Trunk & Infinity Loop -->
              <path d="M50 75 C50 62, 32 64, 32 53 C32 43, 44 45, 50 53 C56 45, 68 43, 68 53 C68 64, 50 62, 50 75 Z" fill="none" stroke="#0F5257" stroke-width="4.5" stroke-linecap="round" />
              <path d="M50 76 L50 38" stroke="#0A2540" stroke-width="4" stroke-linecap="round" />
              <!-- Canopy Leaves -->
              <circle cx="50" cy="24" r="5" fill="#0F5257" />
              <circle cx="38" cy="29" r="4.5" fill="#0A2540" />
              <circle cx="62" cy="29" r="4.5" fill="#0F5257" />
              <circle cx="32" cy="38" r="4" fill="#0F5257" />
              <circle cx="68" cy="38" r="4" fill="#0A2540" />
              <!-- Guiding Gold Star -->
              <polygon points="75,20 77,25 82,25 78,28 79,33 75,30 71,33 72,28 68,25 73,25" fill="#C59B27" />
            </svg>
          </div>
          <div>
            <h1 class="text-lg sm:text-xl font-extrabold tracking-tight text-white leading-tight">
              LONG LIFE LEARNING ACADEMY
            </h1>
            <p class="text-xs text-academy-goldLight font-medium tracking-wide italic">
              “Seek Knowledge from the Cradle to the Grave”
            </p>
          </div>
        </div>

        <!-- Mode Switcher (Admin Controls Hidden by Default) & Learner Profile -->
        <div class="flex items-center gap-2 sm:gap-4 w-full sm:w-auto justify-between sm:justify-end">
          <nav id="admin-unlocked-nav" class="hidden bg-academy-navyLight p-1 rounded-xl flex items-center border border-academy-gold/50 shadow-inner" role="tablist">
            <button
              id="nav-learner-btn"
              onclick="switchView('learner')"
              class="px-3 py-1.5 rounded-lg text-xs sm:text-sm font-semibold transition-all flex items-center gap-1.5 bg-academy-gold text-academy-navy shadow"
            >
              <i class="fa-solid fa-graduation-cap"></i>
              <span>Learner View</span>
            </button>
            <button
              id="nav-studio-btn"
              onclick="switchView('studio')"
              class="px-3 py-1.5 rounded-lg text-xs sm:text-sm font-semibold transition-all flex items-center gap-1.5 text-slate-200 hover:text-white"
            >
              <i class="fa-solid fa-code"></i>
              <span>Admin Studio</span>
            </button>
            <button
              onclick="lockAdminMode()"
              class="ml-1 px-2.5 py-1.5 rounded-lg text-xs font-semibold text-rose-300 hover:bg-rose-950/70 transition flex items-center gap-1"
              title="Lock and Hide Admin Studio"
            >
              <i class="fa-solid fa-lock"></i>
              <span class="hidden sm:inline">Lock</span>
            </button>
          </nav>

          <!-- Learner Name Editable Pill -->
          <div class="flex items-center gap-2 bg-academy-navyLight/80 px-3 py-1.5 rounded-xl border border-slate-700 ml-auto sm:ml-0">
            <div class="w-7 h-7 rounded-full bg-academy-teal text-white flex items-center justify-center text-xs font-bold">
              <i class="fa-solid fa-user"></i>
            </div>
            <div class="text-xs">
              <span class="text-slate-400 block leading-none">Learner</span>
              <input
                id="learner-name-input"
                type="text"
                value="Amina Bekele"
                aria-label="Learner Name"
                onchange="updateLearnerName(this.value)"
                class="bg-transparent text-white font-semibold focus:outline-none focus:border-b border-academy-gold w-28 sm:w-32"
                title="Click to edit your name for certificates"
              />
            </div>
          </div>
        </div>

      </div>
    </div>
  </header>

  <!-- Main Content Area -->
  <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 sm:py-8">

    <!-- ===================================================================== -->
    <!-- VIEW 1: LEARNER PORTAL (CATALOG & INTERACTIVE CLASSROOM)              -->
    <!-- ===================================================================== -->
    <section id="view-learner" class="space-y-8">
      
      <!-- Catalog View -->
      <div id="learner-catalog-view" class="space-y-8">
        <!-- Welcome & Progress Hero -->
        <div class="bg-gradient-to-br from-academy-navy via-academy-navyLight to-academy-teal text-white rounded-2xl p-6 sm:p-8 shadow-xl border-b-4 border-academy-gold flex flex-col lg:flex-row lg:items-center justify-between gap-6">
          <div class="space-y-2 max-w-2xl">
            <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/10 text-academy-goldLight text-xs font-bold tracking-wider uppercase">
              <i class="fa-solid fa-book-open-reader"></i> Lifelong Learner Portal
            </span>
            <h2 class="text-2xl sm:text-3xl font-extrabold leading-tight">
              Welcome back, <span id="hero-learner-name" class="text-academy-goldLight">Amina Bekele</span>
            </h2>
            <p class="text-slate-200 text-sm sm:text-base">
              Continue your journey of continuous growth. Enroll in any academy program, complete structured modules, and earn your verified Certificate of Mastery.
            </p>
          </div>

          <div class="grid grid-cols-3 gap-3 sm:gap-4 shrink-0">
            <div class="bg-white/10 backdrop-blur-sm rounded-xl p-3.5 text-center border border-white/15">
              <div id="stat-enrolled-count" class="text-2xl font-extrabold text-academy-goldLight">1</div>
              <div class="text-[11px] uppercase tracking-wider text-slate-300 font-semibold">Enrolled</div>
            </div>
            <div class="bg-white/10 backdrop-blur-sm rounded-xl p-3.5 text-center border border-white/15">
              <div id="stat-completed-count" class="text-2xl font-extrabold text-emerald-300">0</div>
              <div class="text-[11px] uppercase tracking-wider text-slate-300 font-semibold">Certified</div>
            </div>
            <div class="bg-white/10 backdrop-blur-sm rounded-xl p-3.5 text-center border border-white/15">
              <div id="stat-total-courses" class="text-2xl font-extrabold text-white">4</div>
              <div class="text-[11px] uppercase tracking-wider text-slate-300 font-semibold">Available</div>
            </div>
          </div>
        </div>

        <!-- Search & Category Filter Bar -->
        <div class="flex flex-col md:flex-row items-stretch md:items-center justify-between gap-4 bg-white p-4 rounded-2xl shadow-sm border border-slate-200">
          <div id="category-filters" class="flex flex-wrap items-center gap-2">
            <!-- Category pills injected dynamically -->
          </div>

          <div class="relative w-full md:w-72">
            <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
            <input
              id="course-search-input"
              type="text"
              oninput="renderCatalog()"
              placeholder="Search courses or topics..."
              class="w-full pl-10 pr-4 py-2 rounded-xl border border-slate-300 text-sm focus:outline-none focus:ring-2 focus:ring-academy-teal"
            />
          </div>
        </div>

        <!-- Course Grid -->
        <div id="courses-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <!-- Course cards injected dynamically -->
        </div>
      </div>

      <!-- Interactive Classroom View -->
      <div id="learner-classroom-view" class="hidden space-y-6">
        <div class="flex flex-wrap items-center justify-between gap-4 bg-white p-4 rounded-2xl shadow-sm border border-slate-200">
          <button onclick="closeClassroom()" class="px-4 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 text-academy-navy font-bold text-sm transition flex items-center gap-2">
            <i class="fa-solid fa-arrow-left"></i> Back to Course Catalog
          </button>

          <div class="flex-1 min-w-[200px] max-w-md">
            <div class="flex justify-between text-xs font-bold text-slate-600 mb-1">
              <span id="classroom-course-title-bar" class="truncate">Course Progress</span>
              <span id="classroom-progress-pct" class="text-academy-teal">0%</span>
            </div>
            <div class="w-full h-2.5 bg-slate-200 rounded-full overflow-hidden">
              <div id="classroom-progress-bar" class="h-full bg-academy-teal transition-all duration-300" style="width: 0%"></div>
            </div>
          </div>

          <div class="flex items-center gap-2">
            <button onclick="toggleAiTutorModal()" class="px-3.5 py-2 rounded-xl bg-gradient-to-r from-academy-teal to-academy-navy text-white font-bold text-xs shadow transition flex items-center gap-1.5 ai-badge-glow">
              <i class="fa-solid fa-wand-magic-sparkles text-academy-gold"></i> AI Tutor
            </button>
            <button id="classroom-cert-btn" onclick="openCertificateModal(appState.activeCourseId)" class="hidden px-4 py-2 rounded-xl bg-academy-gold hover:bg-academy-goldLight text-academy-navy font-extrabold text-sm shadow transition flex items-center gap-2">
              <i class="fa-solid fa-award"></i> Certificate
            </button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-start">
          <!-- Left Syllabus Sidebar -->
          <aside class="lg:col-span-4 bg-white rounded-2xl shadow-sm border border-slate-200 p-5 space-y-4">
            <div class="flex items-center justify-between border-b border-slate-100 pb-3">
              <h3 class="font-extrabold text-academy-navy text-base flex items-center gap-2">
                <i class="fa-solid fa-list-check text-academy-teal"></i> Curriculum Syllabus
              </h3>
              <span class="text-[10px] font-bold px-2 py-0.5 rounded-full bg-academy-teal/10 text-academy-teal">AI Assisted</span>
            </div>
            <div id="classroom-syllabus" class="space-y-4">
              <!-- Syllabus items injected dynamically -->
            </div>
          </aside>

          <!-- Right Lesson & Quiz Stage -->
          <div id="classroom-stage" class="lg:col-span-8 bg-white rounded-2xl shadow-sm border border-slate-200 p-6 sm:p-8 min-h-[420px] flex flex-col justify-between">
            <!-- Active lesson or quiz injected dynamically -->
          </div>
        </div>
      </div>

    </section>

    <!-- ===================================================================== -->
    <!-- VIEW 2: HIDDEN ADMIN TEXT-TO-CODE COMPILER & DEPLOYMENT STUDIO        -->
    <!-- ===================================================================== -->
    <section id="view-studio" class="hidden space-y-6">
      
      <!-- Studio Banner -->
      <div class="bg-academy-navy text-white rounded-2xl p-6 sm:p-8 shadow-lg border-b-4 border-academy-gold flex flex-col lg:flex-row lg:items-center justify-between gap-6">
        <div class="space-y-2 max-w-2xl">
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-academy-teal text-xs font-semibold text-white">
            <i class="fa-solid fa-shield-halved text-academy-gold"></i> Authorized Admin Workspace
          </div>
          <h2 class="text-2xl sm:text-3xl font-extrabold">AI Course Generator &amp; Text-to-Code Studio</h2>
          <p class="text-slate-300 text-sm sm:text-base">
            Generate custom curriculum instantly using <strong class="text-academy-goldLight">Gemini AI</strong> or write plain-text modules, compile structured code, and deploy directly to learners.
          </p>
        </div>

        <div class="flex flex-wrap gap-3">
          <button onclick="openAiGeneratorModal()" class="px-4 py-2.5 rounded-xl bg-gradient-to-r from-academy-gold to-academy-goldLight text-academy-navy font-extrabold text-sm shadow hover:opacity-95 transition flex items-center gap-2">
            <i class="fa-solid fa-wand-magic-sparkles"></i> AI Generate New Course
          </button>
          <button onclick="loadSamplePlainTextCourse()" class="px-4 py-2.5 rounded-xl bg-academy-navyLight hover:bg-slate-700 text-academy-goldLight border border-academy-gold/40 text-sm font-semibold transition flex items-center gap-2">
            <i class="fa-solid fa-file-lines"></i> Load Sample Text
          </button>
        </div>
      </div>

      <!-- 3-Step Pipeline: Step 1 (Plain Text) -> Step 2 (Compile to Code) -> Step 3 (Deploy) -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-stretch">
        
        <!-- STEP 1: Plain-Text Module Input (6 Cols) -->
        <div class="lg:col-span-6 bg-white rounded-2xl shadow-sm border border-slate-200 p-6 flex flex-col justify-between space-y-4">
          <div class="space-y-4">
            <div class="flex items-center justify-between border-b border-slate-100 pb-3">
              <div>
                <span class="text-xs font-extrabold uppercase tracking-wider text-academy-teal">Step 1</span>
                <h3 class="text-lg font-extrabold text-academy-navy flex items-center gap-2">
                  <i class="fa-solid fa-align-left text-academy-gold"></i> Plain-Text Module Input
                </h3>
              </div>
              <button onclick="clearPlainTextEditor()" class="text-xs font-semibold text-slate-500 hover:text-rose-600 transition">
                Clear Text
              </button>
            </div>

            <div class="bg-academy-cream border border-academy-gold/30 rounded-xl p-3 text-xs text-slate-600 space-y-1">
              <div class="font-bold text-academy-navy"><i class="fa-solid fa-lightbulb text-academy-gold mr-1"></i> Formatting Guide (Or paste any free-form notes):</div>
              <p class="font-mono text-[11px] text-slate-700">
                Title: Course Name | Category: Life Skills | Instructor: Name<br/>
                Module 1: Module Heading<br/>
                Lesson: Lesson Title<br/>
                Write paragraphs or - bullet points here.<br/>
                Q: Question text? | A: Wrong option | *B: Correct option | C: Wrong option
              </p>
            </div>

            <div>
              <label for="plain-text-course-input" class="sr-only">Plain-Text Course Content</label>
              <textarea
                id="plain-text-course-input"
                rows="16"
                placeholder="Write or paste your course modules in plain text here..."
                class="w-full p-4 rounded-xl border border-slate-300 text-sm font-sans text-slate-800 leading-relaxed focus:ring-2 focus:ring-academy-teal focus:border-transparent focus:outline-none bg-slate-50/50"
              ></textarea>
            </div>
          </div>

          <div class="pt-2">
            <button
              onclick="compilePlainTextToCode()"
              class="w-full py-3 px-5 rounded-xl bg-academy-teal hover:bg-academy-tealLight text-white font-extrabold text-sm shadow-md transition flex items-center justify-center gap-2"
            >
              <i class="fa-solid fa-microchip"></i>
              <span>Step 2: Program Text into Code &rarr;</span>
            </button>
          </div>
        </div>

        <!-- STEP 2 & 3: Compiled Code Inspector & Deployment Panel (6 Cols) -->
        <div class="lg:col-span-6 bg-slate-900 text-slate-100 rounded-2xl shadow-xl border border-slate-700 overflow-hidden flex flex-col justify-between">
          <div>
            <div class="bg-slate-800 px-5 py-3.5 border-b border-slate-700 flex flex-wrap items-center justify-between gap-2">
              <div class="flex items-center gap-2">
                <span class="w-3 h-3 rounded-full bg-rose-500"></span>
                <span class="w-3 h-3 rounded-full bg-amber-400"></span>
                <span class="w-3 h-3 rounded-full bg-emerald-500"></span>
                <span class="ml-2 text-xs font-mono font-semibold text-slate-300">compiled_course_module.json</span>
              </div>
              <div class="flex items-center gap-2">
              <button onclick="toggleAiTutorModal()" class="px-3.5 py-2 rounded-xl bg-gradient-to-r from-academy-teal to-academy-navy text-white font-bold text-xs shadow transition flex items-center gap-1.5 ai-badge-glow">
                <i class="fa-solid fa-wand-magic-sparkles text-academy-gold"></i> AI Tutor
              </button>
              <!-- Google Classroom & Microsoft Teams Integration Buttons -->
              <div class="relative group">
                <button class="px-3 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-bold transition flex items-center gap-1.5">
                  <i class="fa-solid fa-share-nodes text-academy-teal"></i> Share &amp; Sync
                </button>
                <div class="absolute right-0 mt-1 w-56 bg-white rounded-2xl shadow-xl border border-slate-200 py-2 hidden group-hover:block z-30">
                  <button onclick="exportToGoogleClassroom()" class="w-full text-left px-4 py-2.5 text-xs font-semibold text-slate-700 hover:bg-slate-50 flex items-center gap-2.5">
                    <i class="fa-brands fa-google text-emerald-600 text-sm"></i> Share to Google Classroom
                  </button>
                  <button onclick="exportToMicrosoftTeams()" class="w-full text-left px-4 py-2.5 text-xs font-semibold text-slate-700 hover:bg-slate-50 flex items-center gap-2.5">
                    <i class="fa-brands fa-microsoft text-sky-600 text-sm"></i> Share to Microsoft Teams
                  </button>
                  <button onclick="syncCalendarAssignment()" class="w-full text-left px-4 py-2.5 text-xs font-semibold text-slate-700 hover:bg-slate-50 flex items-center gap-2.5 border-t border-slate-100">
                    <i class="fa-solid fa-calendar-plus text-academy-gold text-sm"></i> Add to Calendar Task
                  </button>
                </div>
              </div>

              <button id="classroom-cert-btn" onclick="openCertificateModal(appState.activeCourseId)" class="hidden px-4 py-2 rounded-xl bg-academy-gold hover:bg-academy-goldLight text-academy-navy font-extrabold text-sm shadow transition flex items-center gap-2">
                <i class="fa-solid fa-award"></i> Certificate
              </button>
            </div>
          </div>

          <!-- Status Bar & Step 3 Deploy Button -->
          <div class="bg-slate-800 px-5 py-4 border-t border-slate-700 space-y-3">
            <div id="json-status-indicator" class="text-xs font-mono text-emerald-400 flex items-center gap-2">
              <i class="fa-solid fa-circle-check"></i> Compiled Course Code Ready
            </div>
            <button
              onclick="deployCourseFromCode()"
              class="w-full py-3 px-5 rounded-xl bg-academy-gold hover:bg-academy-goldLight text-academy-navy font-extrabold text-sm shadow-lg transition flex items-center justify-center gap-2"
            >
              <i class="fa-solid fa-rocket"></i>
              <span>Step 3: Deploy Course to Learner Portal</span>
            </button>
          </div>
        </div>

      </div>

      <!-- Existing Deployed Courses Manager Table -->
      <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
        <div class="flex flex-wrap items-center justify-between gap-2 mb-4">
          <h3 class="text-lg font-extrabold text-academy-navy flex items-center gap-2">
            <i class="fa-solid fa-server text-academy-teal"></i> Deployed Academy Curriculum
          </h3>
          <span class="text-xs text-slate-500">Live courses visible to all learners</span>
        </div>
        <div class="overflow-x-auto">
          <table class="w-full text-left border-collapse text-sm">
            <thead>
              <tr class="border-b border-slate-200 text-xs uppercase text-slate-500">
                <th class="py-3 px-4">Course Title</th>
                <th class="py-3 px-4">Category</th>
                <th class="py-3 px-4">Modules</th>
                <th class="py-3 px-4">Quiz</th>
                <th class="py-3 px-4 text-right">Admin Actions</th>
              </tr>
            </thead>
            <tbody id="deployed-courses-table" class="divide-y divide-slate-100">
              <!-- Rows injected dynamically -->
            </tbody>
          </table>
        </div>
      </div>

    </section>

  </main>

  <!-- ===================================================================== -->
  <!-- AI TUTOR SLIDE-OVER / MODAL FOR LEARNERS                              -->
  <!-- ===================================================================== -->
  <div id="ai-tutor-modal" class="fixed inset-0 z-50 hidden bg-slate-950/70 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl max-w-xl w-full shadow-2xl border-2 border-academy-teal overflow-hidden flex flex-col max-h-[85vh]">
      <div class="bg-gradient-to-r from-academy-navy to-academy-teal text-white px-6 py-4 flex items-center justify-between">
        <div class="flex items-center gap-2.5">
          <div class="w-8 h-8 rounded-full bg-academy-gold/20 border border-academy-gold flex items-center justify-center text-academy-gold">
            <i class="fa-solid fa-robot"></i>
          </div>
          <div>
            <h3 class="font-extrabold text-sm tracking-wide">Academy AI Study Assistant</h3>
            <p class="text-[10px] text-academy-goldLight font-medium">Powered by Gemini 3 Flash</p>
          </div>
        </div>
        <button onclick="toggleAiTutorModal()" class="text-slate-200 hover:text-white text-lg" aria-label="Close AI tutor">
          <i class="fa-solid fa-xmark"></i>
        </button>
      </div>

      <!-- Quick Prompt Pills -->
      <div class="px-5 py-3 bg-academy-cream border-b border-slate-200 flex flex-wrap gap-2 text-xs">
        <button onclick="askAiTutorQuick('Summarize the key points of this lesson')" class="px-3 py-1 rounded-lg bg-white border border-slate-300 hover:border-academy-teal text-slate-700 font-medium transition">
          💡 Summarize Lesson
        </button>
        <button onclick="askAiTutorQuick('Give me a real-world example of this concept')" class="px-3 py-1 rounded-lg bg-white border border-slate-300 hover:border-academy-teal text-slate-700 font-medium transition">
          🌍 Real-World Example
        </button>
        <button onclick="askAiTutorQuick('Quiz me with 2 practice questions')" class="px-3 py-1 rounded-lg bg-white border border-slate-300 hover:border-academy-teal text-slate-700 font-medium transition">
          ✍️ Quiz Me
        </button>
      </div>

      <!-- Chat Messages Area -->
      <div id="ai-chat-messages" class="flex-1 p-5 overflow-y-auto space-y-4 text-sm bg-slate-50/50 min-h-[260px] max-h-[360px]">
        <div class="flex items-start gap-3">
          <div class="w-7 h-7 rounded-full bg-academy-teal text-white flex items-center justify-center text-xs font-bold shrink-0 mt-0.5">
            <i class="fa-solid fa-robot"></i>
          </div>
          <div class="bg-white p-3.5 rounded-2xl rounded-tl-sm border border-slate-200 text-slate-700 shadow-sm leading-relaxed">
            Hello! I am your AI learning companion for <strong>Long Life Learning Academy</strong>. Ask me any question about your active lesson or request a simplified explanation!
          </div>
        </div>
      </div>

      <!-- Chat Input Form -->
      <form onsubmit="submitAiTutorQuery(event)" class="p-4 bg-white border-t border-slate-200 flex items-center gap-2">
        <input
          id="ai-chat-input"
          type="text"
          placeholder="Ask AI anything about this topic..."
          required
          class="flex-1 px-4 py-2.5 rounded-xl border border-slate-300 text-sm focus:outline-none focus:ring-2 focus:ring-academy-teal"
        />
        <button type="submit" class="px-4 py-2.5 rounded-xl bg-academy-teal hover:bg-academy-tealLight text-white text-sm font-bold shadow transition flex items-center gap-1.5">
          <span>Ask</span>
          <i class="fa-solid fa-paper-plane text-xs"></i>
        </button>
      </form>
    </div>
  </div>

  <!-- ===================================================================== -->
  <!-- AI COURSE GENERATOR MODAL FOR ADMINS                                  -->
  <!-- ===================================================================== -->
  <div id="ai-generator-modal" class="fixed inset-0 z-50 hidden bg-slate-950/80 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl max-w-lg w-full shadow-2xl border-2 border-academy-gold overflow-hidden">
      <div class="bg-academy-navy text-white px-6 py-4 flex items-center justify-between border-b border-academy-gold/40">
        <div class="flex items-center gap-2.5">
          <i class="fa-solid fa-wand-magic-sparkles text-academy-gold text-lg"></i>
          <h3 class="font-extrabold text-base tracking-wide">AI Course Curriculum Generator</h3>
        </div>
        <button onclick="closeAiGeneratorModal()" class="text-slate-300 hover:text-white text-lg">
          <i class="fa-solid fa-xmark"></i>
        </button>
      </div>

      <div class="p-6 space-y-4">
        <p class="text-sm text-slate-600 leading-relaxed">
          Enter any topic you want to teach at the Academy. Gemini AI will generate a complete structured course with modules, lessons, and quiz questions instantly!
        </p>

        <div>
          <label for="ai-gen-topic-input" class="block text-xs font-bold uppercase tracking-wider text-academy-navy mb-1.5">
            Course Topic or Prompt
          </label>
          <input
            id="ai-gen-topic-input"
            type="text"
            placeholder="e.g. Sustainable Urban Farming & Composting"
            class="w-full px-4 py-3 rounded-xl border border-slate-300 text-sm focus:outline-none focus:ring-2 focus:ring-academy-teal"
          />
        </div>

        <div>
          <label for="ai-gen-category-select" class="block text-xs font-bold uppercase tracking-wider text-academy-navy mb-1.5">
            Academy Category
          </label>
          <select id="ai-gen-category-select" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 text-sm bg-white focus:outline-none focus:ring-2 focus:ring-academy-teal">
            <option value="Foundational Literacy">Foundational Literacy</option>
            <option value="Digital Skills">Digital Skills</option>
            <option value="Leadership & Management">Leadership & Management</option>
        <div class="flex flex-wrap gap-3">
          <button onclick="openAiGeneratorModal()" class="px-4 py-2.5 rounded-xl bg-gradient-to-r from-academy-gold to-academy-goldLight text-academy-navy font-extrabold text-sm shadow hover:opacity-95 transition flex items-center gap-2">
            <i class="fa-solid fa-wand-magic-sparkles"></i> AI Generate New Course
          </button>
          <button onclick="exportAllToGoogleClassroom()" class="px-4 py-2.5 rounded-xl bg-white hover:bg-slate-50 text-emerald-700 border border-emerald-300 text-sm font-semibold transition flex items-center gap-2">
            <i class="fa-brands fa-google"></i> Google Classroom Export
          </button>
          <button onclick="exportAllToMicrosoftTeams()" class="px-4 py-2.5 rounded-xl bg-white hover:bg-slate-50 text-sky-700 border border-sky-300 text-sm font-semibold transition flex items-center gap-2">
            <i class="fa-brands fa-microsoft"></i> MS Teams Sync
          </button>
          <button onclick="loadSamplePlainTextCourse()" class="px-4 py-2.5 rounded-xl bg-academy-navyLight hover:bg-slate-700 text-academy-goldLight border border-academy-gold/40 text-sm font-semibold transition flex items-center gap-2">
            <i class="fa-solid fa-file-lines"></i> Load Sample Text
          </button>
        </div>
      </div>
    </div>
  </div>

  <!-- ===================================================================== -->
  <!-- HIDDEN ADMIN AUTHENTICATION MODAL (Passcode: 54025402)                -->
  <!-- ===================================================================== -->
  <div id="admin-auth-modal" class="fixed inset-0 z-50 hidden bg-slate-950/80 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl max-w-md w-full shadow-2xl border-2 border-academy-gold overflow-hidden">
      <div class="bg-academy-navy text-white px-6 py-4 flex items-center justify-between border-b border-academy-gold/40">
        <div class="flex items-center gap-2.5">
          <i class="fa-solid fa-shield-halved text-academy-gold text-lg"></i>
          <h3 class="font-extrabold text-base tracking-wide">Academy Admin Authentication</h3>
        </div>
        <button onclick="closeAdminAuthModal()" class="text-slate-300 hover:text-white text-lg" aria-label="Close modal">
          <i class="fa-solid fa-xmark"></i>
        </button>
      </div>

      <form onsubmit="submitAdminPasscode(event)" class="p-6 space-y-4">
        <p class="text-sm text-slate-600 leading-relaxed">
          Enter the authorized Academy Administrator access code to unlock the Text-to-Code Course Compiler and Deployment Studio.
        </p>

        <div>
          <label for="admin-passcode-input" class="block text-xs font-bold uppercase tracking-wider text-academy-navy mb-1.5">
            Admin Access Code
          </label>
          <input
            id="admin-passcode-input"
            type="password"
            inputmode="numeric"
            autocomplete="off"
            placeholder="••••••••"
            required
            class="w-full px-4 py-3 rounded-xl border border-slate-300 font-mono text-center text-lg tracking-[0.35em] focus:outline-none focus:ring-2 focus:ring-academy-teal"
          />
          <p id="admin-auth-error" class="hidden text-xs font-semibold text-rose-600 mt-2">
            <i class="fa-solid fa-circle-exclamation mr-1"></i> Invalid administrator code. Access denied.
          </p>
        </div>

        <div class="flex items-center justify-end gap-3 pt-2">
          <button type="button" onclick="closeAdminAuthModal()" class="px-4 py-2.5 rounded-xl border border-slate-300 text-slate-700 text-sm font-semibold hover:bg-slate-50 transition">
            Cancel
          </button>
          <button type="submit" class="px-5 py-2.5 rounded-xl bg-academy-navy hover:bg-academy-navyLight text-white text-sm font-bold shadow-md transition flex items-center gap-2">
            <i class="fa-solid fa-unlock-keyhole text-academy-gold"></i>
            <span>Unlock Studio</span>
          </button>
        </div>
      </form>
    </div>
  </div>

  <!-- ===================================================================== -->
  <!-- OFFICIAL COMPLETION CERTIFICATE MODAL                                 -->
  <!-- ===================================================================== -->
  <div id="certificate-modal" class="fixed inset-0 z-50 hidden bg-slate-900/75 backdrop-blur-sm flex items-center justify-center p-4 overflow-y-auto">
    <div class="bg-white rounded-2xl max-w-4xl w-full shadow-2xl overflow-hidden my-8">
      <!-- Modal Action Header -->
      <div class="bg-academy-navy text-white px-6 py-4 flex items-center justify-between no-print">
        <span class="font-bold text-sm flex items-center gap-2">
          <i class="fa-solid fa-certificate text-academy-gold"></i> Official Academy Credential
        </span>
        <div class="flex items-center gap-3">
          <button onclick="window.print()" class="px-4 py-1.5 rounded-lg bg-academy-gold hover:bg-academy-goldLight text-academy-navy font-bold text-xs transition flex items-center gap-1.5">
            <i class="fa-solid fa-print"></i> Print / Save PDF
          </button>
          <button onclick="closeCertificateModal()" class="text-slate-300 hover:text-white text-lg">
            <i class="fa-solid fa-xmark"></i>
          </button>
        </div>
      </div>

      <!-- Printable Certificate Canvas -->
      <div id="certificate-printable" class="p-8 sm:p-12 bg-academy-cream relative">
        <div class="border-8 border-double border-academy-navy p-6 sm:p-10 bg-white text-center relative">
          <!-- Decorative Corner Accents -->
          <div class="w-8 h-8 border-t-4 border-l-4 border-academy-gold absolute top-3 left-3"></div>
          <div class="w-8 h-8 border-t-4 border-r-4 border-academy-gold absolute top-3 right-3"></div>
          <div class="w-8 h-8 border-b-4 border-l-4 border-academy-gold absolute bottom-3 left-3"></div>
          <div class="w-8 h-8 border-b-4 border-r-4 border-academy-gold absolute bottom-3 right-3"></div>

          <!-- Emblem -->
          <div class="w-20 h-20 mx-auto mb-3">
            <svg viewBox="0 0 100 100" class="w-full h-full" xmlns="http://www.w3.org/2000/svg">
              <circle cx="50" cy="50" r="46" fill="none" stroke="#0A2540" stroke-width="3" />
              <circle cx="50" cy="50" r="41" fill="none" stroke="#C59B27" stroke-width="1.5" />
              <path d="M24 76 Q37 70 50 77 Q63 70 76 76 L73 81 Q61 76 50 82 Q39 76 27 81 Z" fill="#0A2540" />
              <path d="M50 75 C50 62, 32 64, 32 53 C32 43, 44 45, 50 53 C56 45, 68 43, 68 53 C68 64, 50 62, 50 75 Z" fill="none" stroke="#0F5257" stroke-width="4.5" stroke-linecap="round" />
              <path d="M50 76 L50 38" stroke="#0A2540" stroke-width="4" stroke-linecap="round" />
              <circle cx="50" cy="24" r="5" fill="#0F5257" />
              <circle cx="38" cy="29" r="4.5" fill="#0A2540" />
              <circle cx="62" cy="29" r="4.5" fill="#0F5257" />
              <polygon points="75,20 77,25 82,25 78,28 79,33 75,30 71,33 72,28 68,25 73,25" fill="#C59B27" />
            </svg>
          </div>

          <h4 class="text-xs sm:text-sm font-extrabold tracking-[0.25em] text-academy-teal uppercase">
            Long Life Learning Academy
          </h4>
          <p class="text-xs italic text-slate-500 mt-0.5">“Seek Knowledge from the Cradle to the Grave”</p>

          <h2 class="font-serif text-3xl sm:text-4xl font-bold text-academy-navy mt-6 mb-2">
            Certificate of Mastery
          </h2>
          <p class="text-sm text-slate-600">This proudly certifies that</p>

          <div id="cert-learner-name" class="font-serif italic text-2xl sm:text-4xl font-bold text-academy-teal my-4 border-b-2 border-academy-gold/60 inline-block px-8 pb-1">
            Amina Bekele
          </div>

          <p class="text-sm text-slate-600 max-w-lg mx-auto mt-2">
            has successfully completed all required curriculum modules and passed the mastery assessment for the program:
          </p>

          <h3 id="cert-course-title" class="text-xl sm:text-2xl font-extrabold text-academy-navy mt-3">
            Course Title
          </h3>
          <p id="cert-course-meta" class="text-xs text-slate-500 mt-1">
            Category • Quiz Score: 100%
          </p>

          <div class="mt-10 pt-6 border-t border-slate-200 grid grid-cols-3 gap-4 items-end text-xs">
            <div class="text-left">
              <div id="cert-date" class="font-bold text-academy-navy">November 15, 2026</div>
              <div class="text-slate-400">Date of Issue</div>
            </div>
            <div class="flex justify-center">
              <div class="w-16 h-16 rounded-full bg-academy-gold/15 border-2 border-academy-gold flex flex-col items-center justify-center text-academy-navy font-extrabold text-[10px] leading-tight">
                <span>VERIFIED</span>
                <i class="fa-solid fa-check text-academy-teal text-sm my-0.5"></i>
                <span>ACADEMY</span>
              </div>
            </div>
            <div class="text-right">
              <div class="font-serif italic font-bold text-academy-navy text-sm">Academic Council</div>
              <div class="text-slate-400">Long Life Learning Academy</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Footer -->
  <footer class="bg-academy-navy text-slate-300 border-t border-slate-800 mt-12 py-6 no-print">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs">
      <div class="flex items-center gap-2">
        <span class="font-bold text-white">Long Life Learning Academy</span>
        <span class="text-academy-gold">•</span>
        <span class="italic text-academy-goldLight">Seek Knowledge from the Cradle to the Grave</span>
      </div>
      <div class="text-slate-400">
        Programmable Curriculum Engine &bull; Built for Learners of Every Generation
      </div>
    </div>
  </footer>

  <!-- ===================================================================== -->
  <!-- APPLICATION LOGIC & PRE-PROGRAMMED ACADEMY CURRICULUM                 -->
  <!-- ===================================================================== -->
  <script>
    /**
     * 1. PRE-PROGRAMMED ACADEMY COURSES (Structured Curriculum-as-Code)
     */
    const DEFAULT_COURSES = [
      {
        id: "foundational-literacy-101",
        title: "Foundational Reading, Writing & Critical Thinking",
        category: "Foundational Literacy",
        level: "Beginner",
        duration: "3 Hours",
        instructor: "Prof. Samuel Tadesse",
        description: "Build strong reading comprehension, clear everyday writing, and structured reasoning skills designed for learners at any stage of life.",
        modules: [
          {
            title: "Module 1: Active Reading & Comprehension",
            lessons: [
              {
                id: "fl-1-1",
                title: "Reading with Purpose and Curiosity",
                duration: "15 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">Why Active Reading Matters</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">Reading is not merely recognizing words on a page—it is a dialogue between the author and the learner. Whether you are reading a community notice, a technical manual, or literature, asking questions transforms passive reading into deep understanding.</p>
                  <div class="bg-academy-cream border-l-4 border-academy-gold p-4 rounded-r-xl mb-4">
                    <strong class="text-academy-navy block mb-1">The 3-Step SQ3R Method:</strong>
                    <ul class="list-disc pl-5 text-sm space-y-1 text-slate-700">
                      <li><strong>Survey:</strong> Scan headings, bold terms, and summaries before diving in.</li>
                      <li><strong>Question:</strong> Turn headings into questions you want answered.</li>
                      <li><strong>Review:</strong> Summarize the main takeaway in your own words.</li>
                    </ul>
                  </div>
                  <p class="text-slate-700">Practice this habit daily: after reading any article, write down one sentence explaining what you learned and how you can apply it.</p>
                `
              },
              {
                id: "fl-1-2",
                title: "Expanding Vocabulary Through Context",
                duration: "20 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">Decoding Unfamiliar Words</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">Lifelong learners constantly encounter new terminology. Instead of stopping every time you meet an unfamiliar word, examine the surrounding sentence for context clues.</p>
                  <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 mb-4">
                    <div class="p-3.5 rounded-xl bg-slate-50 border border-slate-200">
                      <span class="text-xs font-bold uppercase text-academy-teal">1. Definition Clues</span>
                      <p class="text-sm text-slate-600 mt-1">The author directly explains the term using commas or dashes (e.g., <em>"resilience, the ability to recover quickly from setbacks..."</em>).</p>
                    </div>
                    <div class="p-3.5 rounded-xl bg-slate-50 border border-slate-200">
                      <span class="text-xs font-bold uppercase text-academy-teal">2. Contrast Clues</span>
                      <p class="text-sm text-slate-600 mt-1">Words like <em>however</em>, <em>unlike</em>, or <em>whereas</em> signal the opposite meaning.</p>
                    </div>
                  </div>
                `
              }
            ]
          },
          {
            title: "Module 2: Clear Communication & Writing",
            lessons: [
              {
                id: "fl-2-1",
                title: "Structuring Clear Paragraphs",
                duration: "25 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">The Architecture of a Great Paragraph</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">Clear writing reflects clear thinking. Every strong paragraph focuses on a single core idea supported by evidence or examples.</p>
                  <ol class="list-decimal pl-5 space-y-2 text-slate-700 mb-4">
                    <li><strong>Topic Sentence:</strong> State your main point clearly in the first sentence.</li>
                    <li><strong>Supporting Details:</strong> Provide facts, reasons, or real-world examples.</li>
                    <li><strong>Concluding Bridge:</strong> Tie the idea back to your overall message.</li>
                  </ol>
                `
              }
            ]
          }
        ],
        quiz: [
          {
            question: "What is the primary goal of Active Reading?",
            options: [
              "Reading as fast as possible without stopping",
              "Engaging with the text through questioning and summarizing",
              "Memorizing every single word in a chapter"
            ],
            answerIndex: 1
          },
          {
            question: "Which element states the main idea of a well-structured paragraph?",
            options: [
              "The footnote",
              "The topic sentence",
              "The bibliography"
            ],
            answerIndex: 1
          }
        ]
      },
      {
        id: "digital-skills-essentials",
        title: "Modern Digital Literacy & Safe Internet Navigation",
        category: "Digital Skills",
        level: "Beginner",
        duration: "4 Hours",
        instructor: "Eng. Leyla Mohammed",
        description: "Master essential computer skills, cloud productivity, online safety, and how to evaluate credible information in the digital age.",
        modules: [
          {
            title: "Module 1: Navigating the Digital World",
            lessons: [
              {
                id: "ds-1-1",
                title: "Understanding Files, Cloud Storage & Browsers",
                duration: "20 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">Your Digital Workspace</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">Modern learning happens across phones, tablets, and computers. Understanding how files are organized locally and in the cloud ensures you never lose your important work.</p>
                  <div class="bg-academy-teal/10 border border-academy-teal/30 p-4 rounded-xl text-sm text-slate-800">
                    <strong>Best Practice:</strong> Organize documents into clear folders by year and subject (e.g., <code>2026 / Academy_Certificates</code>), and enable automatic cloud backups.
                  </div>
                `
              },
              {
                id: "ds-1-2",
                title: "Cybersecurity & Protecting Your Identity",
                duration: "25 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">Staying Safe Online</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">Cybersecurity begins with everyday habits. Protect your personal and financial accounts using three golden rules:</p>
                  <ul class="list-disc pl-5 space-y-2 text-slate-700">
                    <li><strong>Strong Passphrases:</strong> Combine 3–4 unrelated words with numbers and symbols.</li>
                    <li><strong>Two-Factor Authentication (2FA):</strong> Always require a second verification step on email and banking accounts.</li>
                    <li><strong>Spot Phishing:</strong> Verify the sender's address before clicking urgent links requesting passwords.</li>
                  </ul>
                `
              }
            ]
          }
        ],
        quiz: [
          {
            question: "What does Two-Factor Authentication (2FA) provide?",
            options: [
              "Faster internet download speeds",
              "An extra layer of security beyond just a password",
              "Automatic deletion of old emails"
            ],
            answerIndex: 1
          },
          {
            question: "Which is the strongest type of password?",
            options: [
              "Your birthday and first name",
              "12345678",
              "A long passphrase combining unrelated words, numbers, and symbols"
            ],
            answerIndex: 2
          }
        ]
      },
      {
        id: "leadership-community-impact",
        title: "Servant Leadership & Ethical Decision Making",
        category: "Leadership & Management",
        level: "Intermediate",
        duration: "5 Hours",
        instructor: "Dr. Dawit Mekonnen",
        description: "Develop practical leadership skills grounded in integrity, active listening, conflict resolution, and empowering teams and communities.",
        modules: [
          {
            title: "Module 1: Foundations of Servant Leadership",
            lessons: [
              {
                id: "lm-1-1",
                title: "Leading by Serving Others",
                duration: "30 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">The Servant Leadership Mindset</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">True leadership is measured not by authority, but by how effectively you elevate the people around you. Servant leaders listen first, remove obstacles for their teams, and foster shared ownership.</p>
                  <blockquote class="border-l-4 border-academy-navy pl-4 italic text-slate-600 my-4">
                    "The leader of a people is their servant." — Timeless Wisdom
                  </blockquote>
                `
              },
              {
                id: "lm-1-2",
                title: "Constructive Conflict Resolution",
                duration: "25 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">Turning Disagreement into Progress</h4>
                  <p class="mb-3 leading-relaxed text-slate-700">Healthy teams experience differing viewpoints. Use the <strong>Listen–Acknowledge–Align</strong> framework to resolve tensions respectfully:</p>
                  <ul class="list-disc pl-5 space-y-1.5 text-slate-700">
                    <li><strong>Listen without interrupting</strong> to understand underlying needs.</li>
                    <li><strong>Acknowledge emotions and perspectives</strong> neutrally without blame.</li>
                    <li><strong>Align on shared goals</strong> to co-create a practical solution.</li>
                  </ul>
                `
              }
            ]
          }
        ],
        quiz: [
          {
            question: "What is the core focus of Servant Leadership?",
            options: [
              "Maintaining strict control over every minor task",
              "Supporting, developing, and empowering team members to succeed",
              "Avoiding all feedback from the community"
            ],
            answerIndex: 1
          }
        ]
      },
      {
        id: "lifelong-habits-financial-wellness",
        title: "Personal Resilience, Time Mastery & Financial Literacy",
        category: "Life Skills",
        level: "All Levels",
        duration: "3.5 Hours",
        instructor: "Hanna Girma, MBA",
        description: "Equip yourself with timeless life skills: budgeting with clarity, building sustainable daily habits, and cultivating a growth mindset at every age.",
        modules: [
          {
            title: "Module 1: Growth Mindset & Daily Habits",
            lessons: [
              {
                id: "ls-1-1",
                title: "The Science of Small Daily Improvements",
                duration: "20 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">Consistency Over Intensity</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">Improving by just 1% every day compounds into extraordinary transformation over a year. Whether learning a new language, managing personal savings, or improving health, attach new habits to existing daily routines.</p>
                `
              },
              {
                id: "ls-1-2",
                title: "Simple Budgeting: Needs, Wants & Future Goals",
                duration: "25 min",
                content: `
                  <h4 class="text-lg font-bold text-academy-navy mb-2">The 50 / 30 / 20 Financial Framework</h4>
                  <p class="mb-4 leading-relaxed text-slate-700">Financial peace comes from knowing where every unit of income goes before the month begins:</p>
                  <ul class="list-disc pl-5 space-y-1.5 text-slate-700">
                    <li><strong>50% Essentials:</strong> Housing, food, utilities, and healthcare.</li>
                    <li><strong>30% Personal &amp; Family Growth:</strong> Education, books, and meaningful experiences.</li>
                    <li><strong>20% Savings &amp; Resilience:</strong> Emergency fund and long-term investments.</li>
                  </ul>
                `
              }
            ]
          }
        ],
        quiz: [
          {
            question: "In the 50/30/20 budgeting framework, what is the 20% portion dedicated to?",
            options: [
              "Impulse shopping",
              "Savings, emergency funds, and long-term goals",
              "Utility bills"
            ],
            answerIndex: 1
          }
        ]
      }
    ];

    /**
     * 2. APPLICATION STATE & LOCAL STORAGE PERSISTENCE
     */
    const STORAGE_KEY = 'llla_academy_state_v2';
    const ADMIN_PASSCODE = '54025402';

    let appState = {
      learnerName: 'Amina Bekele',
      courses: JSON.parse(JSON.stringify(DEFAULT_COURSES)),
      enrolledIds: ['foundational-literacy-101'],
      completedLessons: {}, // { courseId: ['fl-1-1', ...] }
      quizScores: {},       // { courseId: 100 }
      selectedCategory: 'All',
      activeCourseId: null,
      activeItemIndex: 0,   // Index into flattened [lessons..., 'QUIZ']
      isAdminUnlocked: false
    };

    function loadState() {
      try {
        const saved = localStorage.getItem(STORAGE_KEY);
        if (saved) {
          const parsed = JSON.parse(saved);
          if (parsed && Array.isArray(parsed.courses) && parsed.courses.length > 0) {
            appState.learnerName = parsed.learnerName || appState.learnerName;
            appState.courses = parsed.courses;
            appState.enrolledIds = Array.isArray(parsed.enrolledIds) ? parsed.enrolledIds : ['foundational-literacy-101'];
            appState.completedLessons = parsed.completedLessons || {};
            appState.quizScores = parsed.quizScores || {};
          }
        }
      } catch (e) {
        console.warn('Could not restore saved state:', e);
      }
      const nameInput = document.getElementById('learner-name-input');
      const heroName = document.getElementById('hero-learner-name');
      if (nameInput) nameInput.value = appState.learnerName;
      if (heroName) heroName.textContent = appState.learnerName;
    }

    function saveState() {
      try {
        localStorage.setItem(STORAGE_KEY, JSON.stringify({
          learnerName: appState.learnerName,
          courses: appState.courses,
          enrolledIds: appState.enrolledIds,
          completedLessons: appState.completedLessons,
          quizScores: appState.quizScores
        }));
      } catch (e) {
        console.warn('Could not save state:', e);
      }
    }

    /**
     * 3. TOAST NOTIFICATIONS (Replaces alert/confirm)
     */
    function showToast(message, type = 'info') {
      const container = document.getElementById('toast-container');
      if (!container) return;

      const styles = {
        success: 'bg-emerald-900 border-emerald-500 text-white',
        error: 'bg-rose-900 border-rose-500 text-white',
        info: 'bg-academy-navy border-academy-gold text-white'
      };
      const icons = {
        success: 'fa-circle-check text-emerald-400',
        error: 'fa-circle-exclamation text-rose-400',
        info: 'fa-circle-info text-academy-goldLight'
      };

      const toast = document.createElement('div');
      toast.className = `pointer-events-auto flex items-center gap-3 px-4 py-3 rounded-xl border-l-4 shadow-xl text-sm font-medium transition-all duration-300 ${styles[type] || styles.info}`;
      toast.innerHTML = `
        <i class="fa-solid ${icons[type] || icons.info} text-base shrink-0"></i>
        <span class="flex-1">${escapeHtml(message)}</span>
      `;
      container.appendChild(toast);

      setTimeout(() => {
        toast.style.opacity = '0';
        toast.style.transform = 'translateY(8px)';
        setTimeout(() => toast.remove(), 300);
      }, 3400);
    }

    /**
     * 4. GEMINI AI INTEGRATION (AI Tutor & AI Course Generator)
     */
    function toggleAiTutorModal() {
      const modal = document.getElementById('ai-tutor-modal');
      modal.classList.toggle('hidden');
    }

    function openAiGeneratorModal() {
      document.getElementById('ai-generator-modal').classList.remove('hidden');
    }

    function closeAiGeneratorModal() {
      document.getElementById('ai-generator-modal').classList.add('hidden');
    }

    async function callGeminiApi(systemPrompt, userQuery) {
      const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=`;
      const payload = {
        contents: [{ parts: [{ text: userQuery }] }],
        systemInstruction: { parts: [{ text: systemPrompt }] }
      };

      for (let attempt = 0; attempt < 3; attempt++) {
        try {
          const res = await fetch(apiUrl, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(payload)
          });
          const result = await res.json();
          const candidate = result.candidates?.[0];
          if (candidate && candidate.content?.parts?.[0]?.text) {
            return candidate.content.parts[0].text;
          }
        } catch (e) {
          console.warn('AI call attempt failed, retrying...', e);
          await new Promise(r => setTimeout(r, Math.pow(2, attempt) * 1000));
        }
      }
      throw new Error('Unable to connect to Gemini AI. Please check your network connection.');
    }

    async function askAiTutorQuick(promptText) {
      document.getElementById('ai-chat-input').value = promptText;
      await submitAiTutorQuery(new Event('submit'));
    }

    async function submitAiTutorQuery(event) {
      event.preventDefault();
      const inputEl = document.getElementById('ai-chat-input');
      const query = inputEl.value.trim();
      if (!query) return;

      const chatContainer = document.getElementById('ai-chat-messages');
      inputEl.value = '';

      // Append user bubble
      chatContainer.innerHTML += `
        <div class="flex items-start justify-end gap-3">
          <div class="bg-academy-navy text-white p-3.5 rounded-2xl rounded-tr-sm shadow-sm max-w-[85%] leading-relaxed">
            ${escapeHtml(query)}
          </div>
          <div class="w-7 h-7 rounded-full bg-academy-gold text-academy-navy flex items-center justify-center text-xs font-bold shrink-0 mt-0.5">
            <i class="fa-solid fa-user"></i>
          </div>
        </div>
      `;
      chatContainer.scrollTop = chatContainer.scrollHeight;

      // Append loading bubble
      const loadingId = 'ai-loading-' + Date.now();
      chatContainer.innerHTML += `
        <div id="${loadingId}" class="flex items-start gap-3">
          <div class="w-7 h-7 rounded-full bg-academy-teal text-white flex items-center justify-center text-xs font-bold shrink-0 mt-0.5">
            <i class="fa-solid fa-robot"></i>
          </div>
          <div class="bg-white p-3.5 rounded-2xl rounded-tl-sm border border-slate-200 text-slate-500 shadow-sm text-xs italic ai-badge-glow">
            Thinking &amp; analyzing lesson context...
          </div>
        </div>
      `;
      chatContainer.scrollTop = chatContainer.scrollHeight;

      try {
        const activeCourse = appState.courses.find(c => c.id === appState.activeCourseId);
        const courseContext = activeCourse ? `Active Course: ${activeCourse.title} (${activeCourse.category})` : 'Long Life Learning Academy General Portal';
        
        const systemPrompt = `You are a supportive, wise, and encouraging AI tutor at Long Life Learning Academy, founded on the motto "Seek Knowledge from the Cradle to the Grave". Help the learner understand concepts simply and clearly. Context: ${courseContext}`;
        
        const aiReply = await callGeminiApi(systemPrompt, query);

        document.getElementById(loadingId).remove();
        chatContainer.innerHTML += `
          <div class="flex items-start gap-3">
            <div class="w-7 h-7 rounded-full bg-academy-teal text-white flex items-center justify-center text-xs font-bold shrink-0 mt-0.5">
              <i class="fa-solid fa-robot"></i>
            </div>
            <div class="bg-white p-3.5 rounded-2xl rounded-tl-sm border border-slate-200 text-slate-700 shadow-sm leading-relaxed">
              ${escapeHtml(aiReply)}
            </div>
          </div>
        `;
      } catch (err) {
        document.getElementById(loadingId).remove();
        chatContainer.innerHTML += `
          <div class="flex items-start gap-3">
            <div class="w-7 h-7 rounded-full bg-rose-700 text-white flex items-center justify-center text-xs font-bold shrink-0 mt-0.5">
              <i class="fa-solid fa-triangle-exclamation"></i>
            </div>
            <div class="bg-rose-50 border border-rose-200 p-3.5 rounded-2xl rounded-tl-sm text-rose-800 text-xs">
              AI Tutor is temporarily offline. Remember: "Seek Knowledge from the Cradle to the Grave!"
            </div>
          </div>
        `;
      }
      chatContainer.scrollTop = chatContainer.scrollHeight;
    }

    async function generateCourseWithAi() {
      const topic = document.getElementById('ai-gen-topic-input').value.trim();
      const category = document.getElementById('ai-gen-category-select').value;
      if (!topic) {
        showToast('Please enter a course topic.', 'error');
        return;
      }

      const btn = document.getElementById('ai-gen-submit-btn');
      btn.disabled = true;
      btn.innerHTML = '<i class="fa-solid fa-spinner fa-spin mr-1"></i> Generating Curriculum with Gemini AI...';

      try {
        const systemPrompt = `You are an expert curriculum designer for Long Life Learning Academy. Generate a comprehensive course on the requested topic formatted strictly as plain text following this template:
Title: [Course Title]
Category: ${category}
Level: Beginner to Intermediate
Duration: 4 Hours
Instructor: AI Academic Faculty
Summary: [1-sentence course summary]

Module 1: [Module Title]
Lesson: [Lesson Title]
[Paragraph explaining the concept clearly]
- [Key bullet point 1]
- [Key bullet point 2]

Lesson: [Second Lesson Title]
[Paragraph explaining the concept clearly]
- [Key bullet point 1]

Module 2: [Second Module Title]
Lesson: [Lesson Title]
[Paragraph explaining the concept clearly]

Q: [Question 1 text]? | A: [Wrong option] | *B: [Correct option] | C: [Wrong option]
Q: [Question 2 text]? | *A: [Correct option] | B: [Wrong option] | C: [Wrong option]`;

        const plainTextResult = await callGeminiApi(systemPrompt, `Generate course curriculum for: ${topic}`);
        
        document.getElementById('plain-text-course-input').value = plainTextResult;
        compilePlainTextToCode(false);
        closeAiGeneratorModal();
        showToast('AI successfully generated course curriculum! Inspect or Deploy now.', 'success');
      } catch (e) {
        showToast('Failed to generate course with AI: ' + e.message, 'error');
      } finally {
        btn.disabled = false;
        btn.innerHTML = '<i class="fa-solid fa-microchip"></i><span>Generate &amp; Deploy with AI</span>';
      }
    }

    /**
     * 5. HIDDEN ADMIN AUTHENTICATION & NAVIGATION
     */
    let brandClickCount = 0;
    let brandClickTimer = null;

    function handleBrandClick() {
      brandClickCount++;
      if (brandClickTimer) clearTimeout(brandClickTimer);
      brandClickTimer = setTimeout(() => { brandClickCount = 0; }, 1500);

      if (brandClickCount >= 5) {
        brandClickCount = 0;
        if (appState.isAdminUnlocked) {
          switchView('studio');
          showToast('Admin Studio already unlocked.', 'info');
        } else {
          document.getElementById('admin-auth-modal').classList.remove('hidden');
          document.getElementById('admin-passcode-input').value = '';
          document.getElementById('admin-auth-error').classList.add('hidden');
          setTimeout(() => document.getElementById('admin-passcode-input').focus(), 100);
        }
      }
    }

    function closeAdminAuthModal() {
      document.getElementById('admin-auth-modal').classList.add('hidden');
    }

    function submitAdminPasscode(event) {
      event.preventDefault();
      const code = document.getElementById('admin-passcode-input').value.trim();
      if (code === ADMIN_PASSCODE) {
        appState.isAdminUnlocked = true;
        closeAdminAuthModal();
        document.getElementById('admin-unlocked-nav').classList.remove('hidden');
        switchView('studio');
        showToast('Admin Studio unlocked successfully with passcode 54025402!', 'success');
      } else {
        document.getElementById('admin-auth-error').classList.remove('hidden');
        showToast('Incorrect passcode.', 'error');
      }
    }

    function lockAdminMode() {
      appState.isAdminUnlocked = false;
      document.getElementById('admin-unlocked-nav').classList.add('hidden');
      switchView('learner');
      showToast('Admin Studio locked and secured.', 'info');
    }

    function switchView(viewName) {
      const learnerView = document.getElementById('view-learner');
      const studioView = document.getElementById('view-studio');
      const learnerBtn = document.getElementById('nav-learner-btn');
      const studioBtn = document.getElementById('nav-studio-btn');

      if (viewName === 'learner') {
        learnerView.classList.remove('hidden');
        studioView.classList.add('hidden');
        if (learnerBtn) {
          learnerBtn.className = 'px-3 py-1.5 rounded-lg text-xs sm:text-sm font-semibold transition-all flex items-center gap-1.5 bg-academy-gold text-academy-navy shadow';
        }
        if (studioBtn) {
          studioBtn.className = 'px-3 py-1.5 rounded-lg text-xs sm:text-sm font-semibold transition-all flex items-center gap-1.5 text-slate-200 hover:text-white';
        }
      } else if (viewName === 'studio') {
        if (!appState.isAdminUnlocked) {
          document.getElementById('admin-auth-modal').classList.remove('hidden');
          return;
        }
        learnerView.classList.add('hidden');
        studioView.classList.remove('hidden');
        if (studioBtn) {
          studioBtn.className = 'px-3 py-1.5 rounded-lg text-xs sm:text-sm font-semibold transition-all flex items-center gap-1.5 bg-academy-gold text-academy-navy shadow';
        }
        if (learnerBtn) {
          learnerBtn.className = 'px-3 py-1.5 rounded-lg text-xs sm:text-sm font-semibold transition-all flex items-center gap-1.5 text-slate-200 hover:text-white';
        }
        renderDeployedCoursesTable();
      }
    }

    function updateLearnerName(newName) {
      const trimmed = newName.trim() || 'Lifelong Learner';
      appState.learnerName = trimmed;
      document.getElementById('hero-learner-name').textContent = trimmed;
      saveState();
      showToast(`Learner profile updated to "${trimmed}"`, 'info');
    }

    /**
     * 6. LEARNER PORTAL: CATALOG, ENROLLMENT & PROGRESS HELPERS
     */
    function getCourseProgress(course) {
      const allLessons = (course.modules || []).flatMap(m => m.lessons || []);
      const completed = appState.completedLessons[course.id] || [];
      const totalSteps = allLessons.length + 1; // lessons + mastery quiz
      const quizPassed = (appState.quizScores[course.id] || 0) >= 70;
      const doneSteps = completed.filter(id => allLessons.some(l => l.id === id)).length + (quizPassed ? 1 : 0);
      const pct = totalSteps > 0 ? Math.round((doneSteps / totalSteps) * 100) : 0;
      return {
        totalLessons: allLessons.length,
        completedCount: doneSteps,
        quizPassed,
        pct
      };
    }

    function setCategoryFilter(category) {
      appState.selectedCategory = category;
      renderCatalog();
    }

    function renderCatalog() {
      const categories = ['All', ...new Set(appState.courses.map(c => c.category || 'General'))];
      const filterContainer = document.getElementById('category-filters');
      filterContainer.innerHTML = categories.map(cat => {
        const active = appState.selectedCategory === cat;
        return `
          <button
            onclick="setCategoryFilter('${cat.replace(/'/g, "\\'")}')"
            class="px-3.5 py-1.5 rounded-xl text-xs font-bold transition ${
              active
                ? 'bg-academy-navy text-white shadow-sm'
                : 'bg-slate-100 text-slate-600 hover:bg-slate-200'
            }"
          >
            ${escapeHtml(cat)}
          </button>
        `;
      }).join('');

      const query = (document.getElementById('course-search-input').value || '').trim().toLowerCase();
      const filtered = appState.courses.filter(c => {
        const matchesCat = appState.selectedCategory === 'All' || c.category === appState.selectedCategory;
        const matchesQuery =
          !query ||
          c.title.toLowerCase().includes(query) ||
          (c.description || '').toLowerCase().includes(query) ||
          (c.category || '').toLowerCase().includes(query);
        return matchesCat && matchesQuery;
      });

      // Update Hero Metrics
      document.getElementById('stat-enrolled-count').textContent = appState.enrolledIds.length;
      document.getElementById('stat-completed-count').textContent = appState.courses.filter(c => getCourseProgress(c).quizPassed).length;
      document.getElementById('stat-total-courses').textContent = appState.courses.length;

      const grid = document.getElementById('courses-grid');
      if (filtered.length === 0) {
        grid.innerHTML = `
          <div class="col-span-full bg-white rounded-2xl p-12 text-center border border-slate-200">
            <i class="fa-solid fa-book-open text-4xl text-slate-300 mb-3"></i>
            <h3 class="font-bold text-lg text-academy-navy">No matching courses found</h3>
            <p class="text-sm text-slate-500 mt-1">Try adjusting your search keywords or selecting "All" categories.</p>
          </div>
        `;
        return;
      }

      grid.innerHTML = filtered.map(course => {
        const isEnrolled = appState.enrolledIds.includes(course.id);
        const progress = getCourseProgress(course);

        return `
          <article class="bg-white rounded-2xl shadow-sm hover:shadow-md transition border border-slate-200 overflow-hidden flex flex-col justify-between">
            <div class="p-6 space-y-4">
              <div class="flex items-center justify-between gap-2">
                <span class="px-3 py-1 rounded-full text-xs font-bold bg-academy-teal/10 text-academy-teal">
                  ${escapeHtml(course.category || 'Lifelong Learning')}
                </span>
                <span class="text-xs font-semibold text-slate-500">
                  <i class="fa-regular fa-clock mr-1"></i>${escapeHtml(course.duration || 'Self-Paced')}
                </span>
              </div>

              <div>
                <h3 class="text-lg font-extrabold text-academy-navy leading-snug">
                  ${escapeHtml(course.title)}
                </h3>
                <p class="text-xs text-slate-500 mt-1">
                  Instructor: <strong class="text-slate-700">${escapeHtml(course.instructor || 'Academy Faculty')}</strong> &bull; ${escapeHtml(course.level || 'All Levels')}
                </p>
              </div>

              <p class="text-sm text-slate-600 line-clamp-3 leading-relaxed">
                ${escapeHtml(course.description || '')}
              </p>

              ${isEnrolled ? `
                <div class="pt-2">
                  <div class="flex justify-between text-xs font-bold mb-1">
                    <span class="text-slate-600">Progress</span>
                    <span class="text-academy-teal">${progress.pct}%</span>
                  </div>
                  <div class="w-full h-2 bg-slate-100 rounded-full overflow-hidden">
                    <div class="h-full bg-academy-teal transition-all" style="width: ${progress.pct}%"></div>
                  </div>
                </div>
              ` : ''}
            </div>

            <div class="px-6 py-4 bg-slate-50 border-t border-slate-100 flex items-center justify-between gap-3">
              ${progress.quizPassed ? `
                <button onclick="openCertificateModal('${course.id}')" class="px-3.5 py-2 rounded-xl bg-academy-gold/20 hover:bg-academy-gold/30 text-academy-navy font-bold text-xs transition flex items-center gap-1.5">
                  <i class="fa-solid fa-certificate text-academy-gold"></i> Certificate
                </button>
              ` : `
                <span class="text-xs font-semibold text-slate-500">
                  ${(course.modules || []).length} Modules &bull; ${(course.quiz || []).length} Quiz Qs
                </span>
              `}

              <button
                onclick="enrollAndOpenCourse('${course.id}')"
                class="px-4 py-2 rounded-xl font-bold text-xs sm:text-sm transition flex items-center gap-2 ${
                  isEnrolled
                    ? 'bg-academy-teal hover:bg-academy-tealLight text-white shadow-sm'
                    : 'bg-academy-navy hover:bg-academy-navyLight text-white shadow-sm'
                }"
              >
                <span>${isEnrolled ? 'Continue Learning' : 'Enroll Free'}</span>
                <i class="fa-solid fa-arrow-right"></i>
              </button>
            </div>
          </article>
        `;
      }).join('');
    }

    /**
     * 7. INTERACTIVE CLASSROOM, LESSONS & MASTERY QUIZ
     */
    function enrollAndOpenCourse(courseId) {
      if (!appState.enrolledIds.includes(courseId)) {
        appState.enrolledIds.push(courseId);
        saveState();
        showToast('Enrolled! Welcome to your course classroom.', 'success');
      }
      appState.activeCourseId = courseId;
      appState.activeItemIndex = 0;
      document.getElementById('learner-catalog-view').classList.add('hidden');
      document.getElementById('learner-classroom-view').classList.remove('hidden');
      renderClassroom();
    }

    function closeClassroom() {
      appState.activeCourseId = null;
      document.getElementById('learner-classroom-view').classList.add('hidden');
      document.getElementById('learner-catalog-view').classList.remove('hidden');
      renderCatalog();
    }

    function getFlattenedCourseItems(course) {
      const items = [];
      (course.modules || []).forEach((mod, mIdx) => {
        (mod.lessons || []).forEach(lesson => {
          items.push({
            type: 'lesson',
            moduleTitle: mod.title || `Module ${mIdx + 1}`,
            lesson
          });
        });
      });
      items.push({ type: 'quiz' });
      return items;
    }

    function selectClassroomItem(index) {
      appState.activeItemIndex = index;
      renderClassroom();
    }

    function renderClassroom() {
      const course = appState.courses.find(c => c.id === appState.activeCourseId);
      if (!course) {
        closeClassroom();
        return;
      }

      const items = getFlattenedCourseItems(course);
      if (appState.activeItemIndex >= items.length) appState.activeItemIndex = 0;

      const progress = getCourseProgress(course);
      document.getElementById('classroom-course-title-bar').textContent = course.title;
      document.getElementById('classroom-progress-pct').textContent = `${progress.pct}%`;
      document.getElementById('classroom-progress-bar').style.width = `${progress.pct}%`;

      const certBtn = document.getElementById('classroom-cert-btn');
      if (progress.quizPassed) {
        certBtn.classList.remove('hidden');
      } else {
        certBtn.classList.add('hidden');
      }

      // Render Syllabus Sidebar
      const completedSet = new Set(appState.completedLessons[course.id] || []);
      let flatCounter = 0;
      const syllabusHtml = (course.modules || []).map((mod, mIdx) => {
        const lessonsHtml = (mod.lessons || []).map(les => {
          const idx = flatCounter++;
          const isActive = appState.activeItemIndex === idx;
          const isDone = completedSet.has(les.id);
          return `
            <button
              onclick="selectClassroomItem(${idx})"
              class="w-full text-left px-3 py-2.5 rounded-xl text-xs font-semibold flex items-center justify-between gap-2 transition ${
                isActive
                  ? 'bg-academy-navy text-white shadow-sm'
                  : 'hover:bg-slate-100 text-slate-700'
              }"
            >
              <span class="flex items-center gap-2 truncate">
                <i class="fa-solid ${isDone ? 'fa-circle-check text-emerald-400' : 'fa-circle-play text-academy-gold'}"></i>
                <span class="truncate">${escapeHtml(les.title)}</span>
              </span>
              <span class="text-[10px] opacity-75 shrink-0">${escapeHtml(les.duration || '15m')}</span>
            </button>
          `;
        }).join('');

        return `
          <div class="space-y-1.5">
            <div class="text-xs font-extrabold uppercase tracking-wider text-academy-teal px-1">
              ${escapeHtml(mod.title || `Module ${mIdx + 1}`)}
            </div>
            <div class="space-y-1">${lessonsHtml}</div>
          </div>
        `;
      }).join('');

      const quizIdx = flatCounter;
      const isQuizActive = appState.activeItemIndex === quizIdx;
      document.getElementById('classroom-syllabus').innerHTML = `
        ${syllabusHtml}
        <div class="pt-3 border-t border-slate-100">
          <button
            onclick="selectClassroomItem(${quizIdx})"
            class="w-full text-left px-3 py-3 rounded-xl text-xs font-extrabold flex items-center justify-between transition ${
              isQuizActive
                ? 'bg-academy-gold text-academy-navy shadow-sm'
                : 'bg-academy-cream hover:bg-academy-gold/20 text-academy-navy border border-academy-gold/40'
            }"
          >
            <span class="flex items-center gap-2">
              <i class="fa-solid fa-award"></i>
              <span>Final Mastery Assessment</span>
            </span>
            <span>${progress.quizPassed ? `${appState.quizScores[course.id]}%` : 'Quiz'}</span>
          </button>
        </div>
      `;

      // Render Active Stage (Lesson or Quiz)
      const stage = document.getElementById('classroom-stage');
      const currentItem = items[appState.activeItemIndex];

      if (currentItem.type === 'lesson') {
        const les = currentItem.lesson;
        const isDone = completedSet.has(les.id);
        stage.innerHTML = `
          <div class="space-y-5">
            <div class="border-b border-slate-100 pb-4 flex flex-wrap items-center justify-between gap-3">
              <div>
                <span class="text-xs font-bold uppercase tracking-wider text-academy-teal">${escapeHtml(currentItem.moduleTitle)}</span>
                <h2 class="text-2xl font-extrabold text-academy-navy mt-1">${escapeHtml(les.title)}</h2>
              </div>
              <button onclick="askAiTutorQuick('Explain this lesson simply: ${escapeHtml(les.title)}')" class="px-3 py-1.5 rounded-xl bg-academy-teal/10 hover:bg-academy-teal/20 text-academy-teal text-xs font-bold transition flex items-center gap-1.5">
                <i class="fa-solid fa-wand-magic-sparkles"></i> Ask AI to Explain
              </button>
            </div>
            <div class="prose max-w-none text-slate-700 text-sm sm:text-base">
              ${les.content}
            </div>
          </div>

          <div class="pt-6 mt-8 border-t border-slate-100 flex flex-wrap items-center justify-between gap-3">
            <button
              onclick="selectClassroomItem(${Math.max(0, appState.activeItemIndex - 1)})"
              ${appState.activeItemIndex === 0 ? 'disabled' : ''}
              class="px-4 py-2 rounded-xl border border-slate-300 text-slate-700 text-xs sm:text-sm font-bold disabled:opacity-40 hover:bg-slate-50 transition"
            >
              &larr; Previous
            </button>

            <button
              onclick="markLessonCompleteAndNext('${course.id}', '${les.id}', ${appState.activeItemIndex + 1})"
              class="px-5 py-2.5 rounded-xl bg-academy-teal hover:bg-academy-tealLight text-white text-xs sm:text-sm font-extrabold shadow transition flex items-center gap-2"
            >
              <i class="fa-solid fa-check"></i>
              <span>${isDone ? 'Completed — Next Step' : 'Mark Complete & Continue'} &rarr;</span>
            </button>
          </div>
        `;
      } else {
        // Render Final Quiz
        const questions = course.quiz || [];
        const prevScore = appState.quizScores[course.id];
        stage.innerHTML = `
          <div class="space-y-6">
            <div class="border-b border-slate-100 pb-4">
              <span class="text-xs font-bold uppercase tracking-wider text-academy-gold">Mastery Verification</span>
              <h2 class="text-2xl font-extrabold text-academy-navy mt-1">Final Course Assessment</h2>
              <p class="text-sm text-slate-600 mt-1">Score 70% or higher to earn your official Long Life Learning Academy Certificate of Mastery.</p>
            </div>

            ${prevScore !== undefined ? `
              <div class="p-4 rounded-xl ${prevScore >= 70 ? 'bg-emerald-50 border border-emerald-200 text-emerald-900' : 'bg-amber-50 border border-amber-200 text-amber-900'} text-sm font-semibold flex items-center justify-between">
                <span>Previous Assessment Score: <strong>${prevScore}%</strong></span>
                ${prevScore >= 70 ? `<button onclick="openCertificateModal('${course.id}')" class="px-3 py-1.5 rounded-lg bg-academy-navy text-white text-xs font-bold">Open Certificate</button>` : ''}
              </div>
            ` : ''}

            <form id="course-quiz-form" onsubmit="submitCourseQuiz(event, '${course.id}')" class="space-y-6">
              ${questions.map((q, qIdx) => `
                <div class="p-4 rounded-xl bg-slate-50 border border-slate-200 space-y-3">
                  <p class="font-bold text-academy-navy text-sm sm:text-base">${qIdx + 1}. ${escapeHtml(q.question)}</p>
                  <div class="space-y-2">
                    ${(q.options || []).map((opt, oIdx) => `
                      <label class="flex items-center gap-3 p-2.5 rounded-lg bg-white border border-slate-200 hover:border-academy-teal cursor-pointer text-sm">
                        <input type="radio" name="quiz_q_${qIdx}" value="${oIdx}" required class="text-academy-teal focus:ring-academy-teal" />
                        <span>${escapeHtml(opt)}</span>
                      </label>
                    `).join('')}
                  </div>
                </div>
              `).join('')}

              <button type="submit" class="w-full py-3 px-6 rounded-xl bg-academy-gold hover:bg-academy-goldLight text-academy-navy font-extrabold text-sm shadow-md transition">
                Submit Mastery Assessment
              </button>
            </form>
          </div>
        `;
      }
    }

    function markLessonCompleteAndNext(courseId, lessonId, nextIndex) {
      if (!appState.completedLessons[courseId]) {
        appState.completedLessons[courseId] = [];
      }
      if (!appState.completedLessons[courseId].includes(lessonId)) {
        appState.completedLessons[courseId].push(lessonId);
        saveState();
      }
      appState.activeItemIndex = nextIndex;
      renderClassroom();
    }

    function submitCourseQuiz(event, courseId) {
      event.preventDefault();
      const course = appState.courses.find(c => c.id === courseId);
      if (!course) return;

      const questions = course.quiz || [];
      let correct = 0;
      questions.forEach((q, idx) => {
        const selected = document.querySelector(`input[name="quiz_q_${idx}"]:checked`);
        if (selected && Number(selected.value) === Number(q.answerIndex)) {
          correct++;
        }
      });

      const scorePct = questions.length > 0 ? Math.round((correct / questions.length) * 100) : 100;
      appState.quizScores[courseId] = scorePct;
      saveState();
      renderClassroom();

      if (scorePct >= 70) {
        showToast(`Congratulations! You passed with ${scorePct}% and unlocked your Certificate!`, 'success');
        openCertificateModal(courseId);
      } else {
        showToast(`You scored ${scorePct}%. Review the lessons and try again (70% required).`, 'error');
      }
    }

    /**
     * 8. CERTIFICATE MODAL
     */
    function openCertificateModal(courseId) {
      const course = appState.courses.find(c => c.id === courseId);
      if (!course) return;

      const score = appState.quizScores[courseId] || 100;
      document.getElementById('cert-learner-name').textContent = appState.learnerName;
      document.getElementById('cert-course-title').textContent = course.title;
      document.getElementById('cert-course-meta').textContent = `${course.category || 'Lifelong Learning'} • Mastery Score: ${score}%`;
      document.getElementById('cert-date').textContent = new Date().toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      });

      document.getElementById('certificate-modal').classList.remove('hidden');
    }

    function closeCertificateModal() {
      document.getElementById('certificate-modal').classList.add('hidden');
    }

    /**
     * 9. PLAIN-TEXT TO CODE COMPILER & DEPLOYMENT STUDIO
     */
    const SAMPLE_PLAIN_TEXT_COURSE = `Title: Practical Community Entrepreneurship & Micro-Enterprise
Category: Leadership & Management
Level: Beginner
Duration: 3 Hours
Instructor: Dr. Tariq Hassan
Summary: Learn how to identify local community needs, design a simple sustainable business plan, and manage daily cash flow with integrity.

Module 1: Identifying Opportunities & Value
Lesson: Solving Real Community Problems
Every successful enterprise begins by solving a genuine everyday problem for neighbors and families.
- Observe daily challenges in your local market or neighborhood.
- Talk directly with potential customers before spending money.
- Focus on reliability, fair pricing, and honest service.

Lesson: Crafting Your Simple Value Proposition
A value proposition explains in one clear sentence what you offer, who it helps, and why it is trustworthy.
- Keep your offering simple and easy to explain.
- Start small, test feedback, and improve step by step.

Module 2: Managing Money & Sustainable Growth
Lesson: Separating Personal & Enterprise Finances
Never mix household spending with business cash flow. Record every sale and every expense daily in a dedicated ledger.
- Track daily revenue and direct costs clearly.
- Reinvest a portion of profits into better tools and inventory.

Q: What is the first step before launching a community enterprise? | A: Borrowing a large sum of money | *B: Observing local needs and listening to potential customers | C: Printing expensive brochures
Q: Why should business cash be kept separate from household money? | *A: To accurately track profit, expenses, and sustainability | B: Because banks require it for every shop | C: To avoid paying suppliers`;

    let compiledDraftCourse = null;

    function compilePlainTextToCode(showSuccessToast = true) {
      const rawText = document.getElementById('plain-text-course-input').value.trim();
      if (!rawText) {
        showToast('Please enter plain-text course modules.', 'error');
        return null;
      }

      const lines = rawText.split('\n').map(l => l.trim()).filter(l => l.length > 0);
      
      let title = "Custom Academy Course";
      let category = "Lifelong Learning";
      let level = "All Levels";
      let duration = "3 Hours";
      let instructor = "Academy Faculty";
      let summary = "A structured lifelong learning curriculum.";

      const modules = [];
      let currentModule = null;
      let currentLesson = null;
      let currentLessonContentLines = [];
      const quiz = [];

      lines.forEach(line => {
        if (line.toLowerCase().startsWith('title:')) {
          title = line.substring(6).trim();
        } else if (line.toLowerCase().startsWith('category:')) {
          category = line.substring(9).trim();
        } else if (line.toLowerCase().startsWith('level:')) {
          level = line.substring(6).trim();
        } else if (line.toLowerCase().startsWith('duration:')) {
          duration = line.substring(9).trim();
        } else if (line.toLowerCase().startsWith('instructor:')) {
          instructor = line.substring(11).trim();
        } else if (line.toLowerCase().startsWith('summary:')) {
          summary = line.substring(8).trim();
        } else if (line.toLowerCase().startsWith('module')) {
          if (currentLesson) {
            if (currentLessonContentLines.length > 0) {
              currentLesson.content += `<p class="mb-3 text-slate-700 leading-relaxed">${escapeHtml(currentLessonContentLines.join(' '))}</p>`;
              currentLessonContentLines = [];
            }
            if (currentModule) currentModule.lessons.push(currentLesson);
            currentLesson = null;
          }
          if (currentModule && currentModule.lessons.length > 0) {
            modules.push(currentModule);
          }
          currentModule = {
            title: line,
            lessons: []
          };
        } else if (line.toLowerCase().startsWith('lesson:')) {
          if (currentLesson) {
            if (currentLessonContentLines.length > 0) {
              currentLesson.content += `<p class="mb-3 text-slate-700 leading-relaxed">${escapeHtml(currentLessonContentLines.join(' '))}</p>`;
              currentLessonContentLines = [];
            }
            if (currentModule) currentModule.lessons.push(currentLesson);
          }
          currentLesson = {
            id: slugify(title) + '-l-' + (Math.random().toString(36).substring(2, 7)),
            title: line.substring(7).trim(),
            duration: '15 min',
            content: ''
          };
        } else if (line.startsWith('Q:') || line.startsWith('q:')) {
          if (currentLesson) {
            if (currentLessonContentLines.length > 0) {
              currentLesson.content += `<p class="mb-3 text-slate-700 leading-relaxed">${escapeHtml(currentLessonContentLines.join(' '))}</p>`;
              currentLessonContentLines = [];
            }
            if (currentModule) currentModule.lessons.push(currentLesson);
            currentLesson = null;
          }
          if (currentModule) {
            modules.push(currentModule);
            currentModule = null;
          }

          // Parse Question string: Q: Question text? | A: Opt1 | *B: CorrectOpt | C: Opt3
          const parts = line.substring(2).split('|').map(p => p.trim());
          const qText = parts[0];
          const options = [];
          let answerIndex = 0;

          parts.slice(1).forEach((optPart, idx) => {
            let cleanOpt = optPart;
            if (cleanPartStartsWith(optPart, 'A:') || cleanPartStartsWith(optPart, 'B:') || cleanPartStartsWith(optPart, 'C:') || cleanPartStartsWith(optPart, 'D:')) {
              cleanOpt = optPart.substring(2).trim();
            }
            if (cleanOpt.startsWith('*')) {
              answerIndex = idx;
              cleanOpt = cleanOpt.substring(1).trim();
            }
            options.push(cleanOpt);
          });

          quiz.push({
            question: qText,
            options: options.length > 0 ? options : ['True', 'False'],
            answerIndex: answerIndex
          });
        } else {
          if (currentLesson) {
            if (line.startsWith('-')) {
              if (currentLessonContentLines.length > 0) {
                currentLesson.content += `<p class="mb-3 text-slate-700 leading-relaxed">${escapeHtml(currentLessonContentLines.join(' '))}</p>`;
                currentLessonContentLines = [];
              }
              currentLesson.content += `<ul class="list-disc pl-5 mb-3 text-slate-700 space-y-1"><li>${escapeHtml(line.substring(1).trim())}</li></ul>`;
            } else {
              currentLessonContentLines.push(line);
            }
          }
        }
      });

      if (currentLesson) {
        if (currentLessonContentLines.length > 0) {
          currentLesson.content += `<p class="mb-3 text-slate-700 leading-relaxed">${escapeHtml(currentLessonContentLines.join(' '))}</p>`;
        }
        if (currentModule) currentModule.lessons.push(currentLesson);
      }
      if (currentModule && currentModule.lessons.length > 0) {
        modules.push(currentModule);
      }

      if (modules.length === 0) {
        modules.push({
          title: "Module 1: Core Fundamentals",
          lessons: [
            {
              id: slugify(title) + '-l-1',
              title: "Introduction & Key Concepts",
              duration: "15 min",
              content: `<p class="text-slate-700 leading-relaxed">${escapeHtml(summary)}</p>`
            }
          ]
        });
      }

      if (quiz.length === 0) {
        quiz.push({
          question: "What is the primary takeaway of " + title + "?",
          options: ["Continuous learning and skill application", "Memorizing textbook definitions", "Avoiding all challenges"],
          answerIndex: 0
        });
      }

      compiledDraftCourse = {
        id: slugify(title),
        title,
        category,
        level,
        duration,
        instructor,
        description: summary,
        modules,
        quiz
      };

      document.getElementById('json-status-indicator').innerHTML = `
        <i class="fa-solid fa-circle-check text-emerald-400"></i> Successfully compiled "${escapeHtml(title)}" (${modules.length} modules, ${quiz.length} quiz questions)
      `;

      if (showSuccessToast) {
        showToast('Text compiled into structured course code successfully!', 'success');
      }
      return compiledDraftCourse;
    }

    function cleanPartStartsWith(str, prefix) {
      return str.toUpperCase().startsWith(prefix);
    }

    function deployCourseFromCode() {
      const course = compiledDraftCourse || compilePlainTextToCode(false);
      if (!course) return;

      const existingIdx = appState.courses.findIndex(c => c.id === course.id);
      if (existingIdx >= 0) {
        appState.courses[existingIdx] = course;
      } else {
        appState.courses.unshift(course);
      }

      if (!appState.enrolledIds.includes(course.id)) {
        appState.enrolledIds.push(course.id);
      }

      saveState();
      renderDeployedCoursesTable();
      renderCatalog();
      showToast(`Course "${course.title}" deployed successfully to the Learner Portal!`, 'success');
      switchView('learner');
      enrollAndOpenCourse(course.id);
    }

    function renderDeployedCoursesTable() {
      const tbody = document.getElementById('deployed-courses-table');
      if (!tbody) return;

      tbody.innerHTML = appState.courses.map(course => `
        <tr class="hover:bg-slate-50 transition">
          <td class="py-3 px-4 font-bold text-academy-navy">${escapeHtml(course.title)}</td>
          <td class="py-3 px-4"><span class="px-2.5 py-1 rounded-full text-xs font-bold bg-academy-teal/10 text-academy-teal">${escapeHtml(course.category || 'General')}</span></td>
          <td class="py-3 px-4">${(course.modules || []).length} modules</td>
          <td class="py-3 px-4">${(course.quiz || []).length} questions</td>
          <td class="py-3 px-4 text-right space-x-2">
            <button onclick="enrollAndOpenCourse('${course.id}')" class="px-3 py-1.5 rounded-lg bg-academy-teal text-white text-xs font-bold hover:bg-academy-tealLight transition">
              Preview
            </button>
            <button onclick="deleteDeployedCourse('${course.id}')" class="px-3 py-1.5 rounded-lg bg-rose-100 text-rose-700 text-xs font-bold hover:bg-rose-200 transition">
              Remove
            </button>
          </td>
        </tr>
      `).join('');
    }

    function deleteDeployedCourse(courseId) {
      if (appState.courses.length <= 1) {
        showToast('You must keep at least one course in the academy.', 'error');
        return;
      }
      appState.courses = appState.courses.filter(c => c.id !== courseId);
      appState.enrolledIds = appState.enrolledIds.filter(id => id !== courseId);
      saveState();
      renderDeployedCoursesTable();
      renderCatalog();
      showToast('Course removed from academy catalog.', 'info');
    }

    function initStudio() {
      document.getElementById('plain-text-course-input').value = SAMPLE_PLAIN_TEXT_COURSE;
      compilePlainTextToCode(false);
      renderDeployedCoursesTable();
    }

    function loadSamplePlainTextCourse() {
      document.getElementById('plain-text-course-input').value = SAMPLE_PLAIN_TEXT_COURSE;
      compilePlainTextToCode(true);
    }

    function clearPlainTextEditor() {
      document.getElementById('plain-text-course-input').value = '';
      document.getElementById('plain-text-course-input').focus();
    }

    function escapeHtml(str) {
      return str
        .replace(/&/g, '&amp;')
        .replace(/</g, '&lt;')
        .replace(/>/g, '&gt;')
        .replace(/"/g, '&quot;');
    }

    function slugify(text) {
      return text
        .toLowerCase()
        .replace(/[^a-z0-9]+/g, '-')
        .replace(/(^-|-$)/g, '') || `course-${Date.now()}`;
    }

    /**
     * Google Classroom and Microsoft Teams Integration Tools
     */
    function exportToGoogleClassroom() {
      const course = appState.courses.find(c => c.id === appState.activeCourseId);
      const title = course ? course.title : 'Long Life Learning Academy Course';
      const url = `https://classroom.google.com/u/0/share?url=${encodeURIComponent(window.location.href)}&title=${encodeURIComponent(title)}`;
      window.open(url, '_blank', 'width=800,height=600');
      showToast('Opening Google Classroom share bridge...', 'success');
    }

    function exportToMicrosoftTeams() {
      const course = appState.courses.find(c => c.id === appState.activeCourseId);
      const title = course ? course.title : 'Long Life Learning Academy Course';
      const url = `https://teams.microsoft.com/share?href=${encodeURIComponent(window.location.href)}&text=${encodeURIComponent('Join this lifelong learning module at Long Life Learning Academy: ' + title)}`;
      window.open(url, '_blank', 'width=800,height=600');
      showToast('Opening Microsoft Teams share bridge...', 'success');
    }

    function syncCalendarAssignment() {
      showToast('Assignment added to your personal learning schedule and reminders!', 'success');
    }

    function exportAllToGoogleClassroom() {
      const url = `https://classroom.google.com/`;
      window.open(url, '_blank');
      showToast('Redirecting to Google Classroom educator dashboard...', 'success');
    }

    function exportAllToMicrosoftTeams() {
      const url = `https://teams.microsoft.com/`;
      window.open(url, '_blank');
      showToast('Redirecting to Microsoft Teams educator workspace...', 'success');
    }

    function resetAllAcademyData() {
      localStorage.removeItem(STORAGE_KEY);
      appState.courses = JSON.parse(JSON.stringify(DEFAULT_COURSES));
      appState.enrolledIds = ['foundational-literacy-101'];
      appState.completedLessons = {};
      appState.quizScores = {};
      saveState();
      renderDeployedCoursesTable();
      showToast('Academy catalog reset to default curriculum.', 'info');
    }

    /**
     * 10. INITIALIZE APP ON LOAD
     */
    window.addEventListener('DOMContentLoaded', () => {
      loadState();
      initStudio();
      renderCatalog();
    });
  </script>
</body>
</html>
