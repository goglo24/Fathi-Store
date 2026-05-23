<!DOCTYPE html>
<html lang="en" class="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fathi Store | Ethio Entrance Exam: Grade 12</title>
    <!-- Tailwind CSS for rapid styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Phosphor Icons for modern iconography -->
    <script src="https://unpkg.com/@phosphor-icons/web"></script>
    <!-- Google Fonts: Inter for clean typography -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chart.js for progress tracking visualization -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f0fdf4',
                            100: '#dcfce7',
                            500: '#22c55e',
                            600: '#16a34a',
                            700: '#15803d',
                            900: '#14532d',
                        },
                        dark: {
                            bg: '#0f172a',
                            surface: '#1e293b',
                            border: '#334155'
                        }
                    },
                    animation: {
                        'fade-in': 'fadeIn 0.3s ease-out',
                        'slide-up': 'slideUp 0.4s ease-out',
                    },
                    keyframes: {
                        fadeIn: {
                            '0%': { opacity: '0' },
                            '100%': { opacity: '1' },
                        },
                        slideUp: {
                            '0%': { opacity: '0', transform: 'translateY(10px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom scrollbar for better aesthetics */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background-color: #cbd5e1;
            border-radius: 20px;
        }
        .dark ::-webkit-scrollbar-thumb {
            background-color: #475569;
        }
        
        /* Smooth transitions for theme switching */
        body {
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        
        /* Hide sections initially except home */
        .app-section {
            display: none;
        }
        .app-section.active {
            display: block;
            animation: fadeIn 0.4s ease-out;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-900 dark:bg-dark-bg dark:text-gray-100 min-h-screen flex flex-col font-sans antialiased">

    <!-- Header / Navigation -->
    <header class="sticky top-0 z-50 bg-white/80 dark:bg-dark-surface/80 backdrop-blur-md border-b border-gray-200 dark:border-dark-border shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <!-- Logo & Branding -->
                <div class="flex items-center gap-3 cursor-pointer" onclick="navigateTo('home')">
                    <div class="w-10 h-10 bg-brand-500 rounded-xl flex items-center justify-center text-white shadow-lg shadow-brand-500/30">
                        <i class="ph ph-graduation-cap text-2xl"></i>
                    </div>
                    <div>
                        <h1 class="text-xl font-bold leading-tight">Fathi Store</h1>
                        <p class="text-xs text-gray-500 dark:text-gray-400 font-medium">Students Assessments</p>
                    </div>
                </div>

                <!-- Desktop Navigation Links -->
                <nav class="hidden md:flex items-center space-x-8">
                    <button onclick="navigateTo('home')" class="nav-btn text-gray-600 dark:text-gray-300 hover:text-brand-600 dark:hover:text-brand-500 font-medium transition-colors active-nav">Home</button>
                    <button onclick="navigateTo('practice')" class="nav-btn text-gray-600 dark:text-gray-300 hover:text-brand-600 dark:hover:text-brand-500 font-medium transition-colors">Practice</button>
                    <button onclick="navigateTo('progress')" class="nav-btn text-gray-600 dark:text-gray-300 hover:text-brand-600 dark:hover:text-brand-500 font-medium transition-colors">Progress</button>
                    <button onclick="navigateTo('exam')" class="nav-btn text-gray-600 dark:text-gray-300 hover:text-brand-600 dark:hover:text-brand-500 font-medium transition-colors">Mock Exam</button>
                </nav>

                <!-- Actions: Dark Mode Toggle & Mobile Menu -->
                <div class="flex items-center gap-4">
                    <button onclick="installApp()" class="install-app-btn hidden px-3 py-1.5 bg-brand-100 dark:bg-brand-900/30 text-brand-700 dark:text-brand-300 hover:bg-brand-200 dark:hover:bg-brand-900/50 text-sm font-semibold rounded-lg transition-colors flex items-center gap-2">
                        <i class="ph ph-download-simple text-lg"></i> Install App
                    </button>

                    <button id="theme-toggle" class="p-2 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors" aria-label="Toggle Dark Mode">
                        <i id="theme-icon" class="ph ph-moon text-xl"></i>
                    </button>
                    
                    <button id="mobile-menu-btn" class="md:hidden p-2 text-gray-600 dark:text-gray-300">
                        <i class="ph ph-list text-2xl"></i>
                    </button>
                </div>
            </div>
        </div>
        
        <!-- Mobile Navigation Menu (Hidden by default) -->
        <div id="mobile-menu" class="hidden md:hidden bg-white dark:bg-dark-surface border-b border-gray-200 dark:border-dark-border">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <button onclick="navigateTo('home', true)" class="block w-full text-left px-3 py-2 rounded-md text-base font-medium text-gray-700 dark:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-800">Home</button>
                <button onclick="navigateTo('practice', true)" class="block w-full text-left px-3 py-2 rounded-md text-base font-medium text-gray-700 dark:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-800">Practice (By Chapter)</button>
                <button onclick="navigateTo('progress', true)" class="block w-full text-left px-3 py-2 rounded-md text-base font-medium text-gray-700 dark:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-800">My Progress</button>
                <button onclick="navigateTo('exam', true)" class="block w-full text-left px-3 py-2 rounded-md text-base font-medium text-gray-700 dark:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-800">Mock Exam</button>
                <button onclick="installApp()" class="install-app-btn hidden w-full text-left px-3 py-2 mt-2 rounded-md text-base font-bold text-brand-600 dark:text-brand-400 bg-brand-50 dark:bg-brand-900/20 hover:bg-brand-100 dark:hover:bg-brand-900/40 flex items-center gap-2">
                    <i class="ph ph-download-simple text-xl"></i> Install Offline App
                </button>
            </div>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="flex-grow w-full max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        
        <!-- ================= HOME SECTION ================= -->
        <section id="section-home" class="app-section active">
            <!-- Hero Banner -->
            <div class="relative bg-white dark:bg-dark-surface rounded-3xl overflow-hidden shadow-xl shadow-brand-500/5 border border-gray-100 dark:border-dark-border mb-12">
                <div class="absolute top-0 right-0 -mt-20 -mr-20 w-80 h-80 bg-brand-500/10 rounded-full blur-3xl"></div>
                <div class="absolute bottom-0 left-0 -mb-20 -ml-20 w-64 h-64 bg-blue-500/10 rounded-full blur-3xl"></div>
                
                <div class="relative z-10 px-6 py-12 md:py-20 md:px-12 flex flex-col md:flex-row items-center justify-between gap-10">
                    <div class="w-full md:w-3/5 space-y-6">
                        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-brand-50 dark:bg-brand-900/30 text-brand-600 dark:text-brand-400 text-sm font-semibold mb-2">
                            <span class="w-2 h-2 rounded-full bg-brand-500 animate-pulse"></span>
                            100% Offline Accessible
                        </div>
                        <h2 class="text-4xl md:text-5xl font-extrabold tracking-tight text-gray-900 dark:text-white leading-tight">
                            Master the <span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-500 to-blue-600">Ethio Entrance Exam</span> Grade 12
                        </h2>
                        <p class="text-lg text-gray-600 dark:text-gray-300 max-w-2xl leading-relaxed">
                            The ultimate preparation tool for Natural and Social Science students. Access years of past exams (2008-2017 EC), detailed explanations, and track your readiness—all without needing an internet connection.
                        </p>
                        <div class="flex flex-wrap gap-4 pt-4">
                            <button onclick="navigateTo('practice')" class="px-6 py-3 bg-brand-600 hover:bg-brand-700 text-white font-medium rounded-xl shadow-lg shadow-brand-500/30 transition-all hover:-translate-y-0.5 flex items-center gap-2">
                                <i class="ph ph-books text-xl"></i> Start Practicing
                            </button>
                            <button onclick="navigateTo('exam')" class="px-6 py-3 bg-white dark:bg-dark-surface text-gray-800 dark:text-gray-200 border border-gray-200 dark:border-dark-border hover:border-brand-500 dark:hover:border-brand-500 font-medium rounded-xl shadow-sm transition-all flex items-center gap-2">
                                <i class="ph ph-timer text-xl"></i> Take Mock Exam
                            </button>
                        </div>
                    </div>
                    
                    <!-- Decorative Graphic -->
                    <div class="w-full md:w-2/5 flex justify-center animate-slide-up">
                        <div class="relative w-72 h-72">
                            <!-- Abstract Representation of App Interface -->
                            <div class="absolute inset-0 bg-gradient-to-br from-brand-100 to-blue-50 dark:from-gray-800 dark:to-dark-surface rounded-2xl shadow-2xl border border-white/50 dark:border-gray-700 transform rotate-3 flex flex-col p-4">
                                <div class="w-full h-8 bg-gray-200/50 dark:bg-gray-700/50 rounded-lg mb-4"></div>
                                <div class="w-3/4 h-4 bg-gray-200/50 dark:bg-gray-700/50 rounded-md mb-2"></div>
                                <div class="w-1/2 h-4 bg-gray-200/50 dark:bg-gray-700/50 rounded-md mb-6"></div>
                                <div class="grid grid-cols-2 gap-3 flex-grow">
                                    <div class="bg-brand-500/20 rounded-xl"></div>
                                    <div class="bg-blue-500/20 rounded-xl"></div>
                                    <div class="bg-purple-500/20 rounded-xl"></div>
                                    <div class="bg-orange-500/20 rounded-xl"></div>
                                </div>
                            </div>
                            <div class="absolute -bottom-4 -left-4 w-24 h-24 bg-yellow-400 rounded-full mix-blend-multiply filter blur-xl opacity-70 animate-blob"></div>
                            <div class="absolute -top-4 -right-4 w-24 h-24 bg-brand-400 rounded-full mix-blend-multiply filter blur-xl opacity-70 animate-blob animation-delay-2000"></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Core Features Grid -->
            <div class="mb-8">
                <h3 class="text-2xl font-bold mb-6 flex items-center gap-2">
                    <i class="ph-fill ph-sparkle text-brand-500"></i> Why Choose Our App
                </h3>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                    <!-- Feature 1 -->
                    <div class="bg-white dark:bg-dark-surface p-6 rounded-2xl border border-gray-100 dark:border-dark-border shadow-sm hover:shadow-md transition-shadow">
                        <div class="w-12 h-12 bg-blue-100 dark:bg-blue-900/30 text-blue-600 dark:text-blue-400 rounded-xl flex items-center justify-center mb-4">
                            <i class="ph ph-database text-2xl"></i>
                        </div>
                        <h4 class="text-lg font-semibold mb-2">Extensive Question Bank</h4>
                        <p class="text-gray-600 dark:text-gray-400 text-sm">Access years of past National Exams from 2008 to 2017 EC, complete with detailed explanations.</p>
                    </div>
                    <!-- Feature 2 -->
                    <div class="bg-white dark:bg-dark-surface p-6 rounded-2xl border border-gray-100 dark:border-dark-border shadow-sm hover:shadow-md transition-shadow">
                        <div class="w-12 h-12 bg-green-100 dark:bg-green-900/30 text-brand-600 dark:text-brand-400 rounded-xl flex items-center justify-center mb-4">
                            <i class="ph ph-funnel text-2xl"></i>
                        </div>
                        <h4 class="text-lg font-semibold mb-2">Chapter-by-Chapter</h4>
                        <p class="text-gray-600 dark:text-gray-400 text-sm">Don't just guess. Filter and practice questions focused on specific units and subjects you need to master.</p>
                    </div>
                    <!-- Feature 3 -->
                    <div class="bg-white dark:bg-dark-surface p-6 rounded-2xl border border-gray-100 dark:border-dark-border shadow-sm hover:shadow-md transition-shadow">
                        <div class="w-12 h-12 bg-purple-100 dark:bg-purple-900/30 text-purple-600 dark:text-purple-400 rounded-xl flex items-center justify-center mb-4">
                            <i class="ph ph-chart-line-up text-2xl"></i>
                        </div>
                        <h4 class="text-lg font-semibold mb-2">Progress Tracking</h4>
                        <p class="text-gray-600 dark:text-gray-400 text-sm">Monitor your statistics visually. Easily identify your strong subjects and areas needing improvement.</p>
                    </div>
                    <!-- Feature 4 -->
                    <div class="bg-white dark:bg-dark-surface p-6 rounded-2xl border border-gray-100 dark:border-dark-border shadow-sm hover:shadow-md transition-shadow">
                        <div class="w-12 h-12 bg-orange-100 dark:bg-orange-900/30 text-orange-600 dark:text-orange-400 rounded-xl flex items-center justify-center mb-4">
                            <i class="ph ph-wifi-slash text-2xl"></i>
                        </div>
                        <h4 class="text-lg font-semibold mb-2">100% Offline</h4>
                        <p class="text-gray-600 dark:text-gray-400 text-sm">Study anywhere, anytime. No internet connection is required once the app is installed.</p>
                    </div>
                </div>
            </div>
            
            <!-- Subject Selection Quick Start -->
            <div>
                <h3 class="text-2xl font-bold mb-6">Quick Start by Stream</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Natural Science -->
                    <div class="relative overflow-hidden rounded-2xl group cursor-pointer" onclick="navigateTo('practice')">
                        <img src="https://images.unsplash.com/photo-1532094349884-543bc11b234d?auto=format&fit=crop&w=800&q=80" alt="Natural Science" class="w-full h-48 object-cover transition-transform duration-500 group-hover:scale-105">
                        <div class="absolute inset-0 bg-gradient-to-t from-gray-900/90 to-gray-900/20 flex flex-col justify-end p-6">
                            <h4 class="text-2xl font-bold text-white mb-1">Natural Sciences</h4>
                            <p class="text-gray-200 text-sm">Physics, Chemistry, Biology, Maths (Nat)</p>
                        </div>
                    </div>
                    <!-- Social Science -->
                    <div class="relative overflow-hidden rounded-2xl group cursor-pointer" onclick="navigateTo('practice')">
                        <img src="https://images.unsplash.com/photo-1455390582262-044cdead27d8?auto=format&fit=crop&w=800&q=80" alt="Social Science" class="w-full h-48 object-cover transition-transform duration-500 group-hover:scale-105">
                        <div class="absolute inset-0 bg-gradient-to-t from-gray-900/90 to-gray-900/20 flex flex-col justify-end p-6">
                            <h4 class="text-2xl font-bold text-white mb-1">Social Sciences</h4>
                            <p class="text-gray-200 text-sm">Geography, History, Economics, Maths (Soc)</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= PRACTICE SECTION ================= -->
        <section id="section-practice" class="app-section">
            <div id="practice-header-text" class="mb-6 flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
                <div>
                    <h2 class="text-3xl font-bold mb-2">Practice by Subject</h2>
                    <p class="text-gray-600 dark:text-gray-400">Select your stream and subject to focus your study.</p>
                </div>
            </div>

            <!-- Stream Selector Tabs -->
            <div id="stream-selector-container" class="flex p-1 bg-gray-200 dark:bg-gray-800 rounded-xl mb-6 w-full max-w-md">
                <button onclick="toggleStream('natural')" id="tab-natural" class="flex-1 py-2 px-4 rounded-lg text-sm font-bold shadow-sm bg-white dark:bg-dark-surface text-brand-600 dark:text-brand-400 transition-all">Natural Science</button>
                <button onclick="toggleStream('social')" id="tab-social" class="flex-1 py-2 px-4 rounded-lg text-sm font-medium text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white transition-all">Social Science</button>
            </div>

            <!-- Subjects Container -->
            <div id="subjects-container" class="mb-8">
                <!-- Natural Subjects Grid -->
                <div id="grid-natural" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 animate-fade-in">
                    <div onclick="openSubject('Physics', 'ph-atom')" class="bg-white dark:bg-dark-surface p-5 rounded-2xl border border-gray-200 dark:border-dark-border shadow-sm hover:shadow-md hover:border-brand-300 dark:hover:border-brand-700 transition-all cursor-pointer group flex items-center gap-4">
                        <div class="w-12 h-12 bg-blue-50 dark:bg-blue-900/20 text-blue-500 rounded-xl flex items-center justify-center text-2xl group-hover:scale-110 transition-transform"><i class="ph ph-atom"></i></div>
                        <div><h4 class="font-bold text-gray-900 dark:text-gray-100">Ph
