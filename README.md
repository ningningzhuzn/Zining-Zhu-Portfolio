<!DOCTYPE html>
<html lang="zh-CN" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KAIROS // 空间研究与室内建筑作品集</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Alpine.js for interactivity -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
    <!-- Google Fonts: Playfair Display & Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        serif: ['"Playfair Display"', 'serif'],
                        sans: ['"Inter"', 'sans-serif'],
                    },
                    colors: {
                        stone: {
                            850: '#1c1917',
                            950: '#0c0a09',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom scrollbar and editorial tweaks */
        body {
            font-family: 'Inter', sans-serif;
        }
        .serif-title {
            font-family: 'Playfair Display', serif;
        }
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0c0a09;
        }
        ::-webkit-scrollbar-thumb {
            background: #292524;
            border-radius: 3px;
        }
    </style>
</head>
<body x-data="{ 
    darkMode: true, 
    activeFilter: 'all', 
    selectedProject: null,
    mobileMenuOpen: false,
    projects: [
        {
            id: 1,
            title: '重影秩序：隐喻与极简序列',
            category: 'Interior Design',
            catSlug: 'interior',
            year: '2025',
            summary: '基于现象学视角的住宅空间重构，探讨光影在纯白体块中的质感流动与情绪沉淀。',
            description: '本项目位于城市边缘，通过减法设计剥离冗余的装饰语言。引入垂直天井与微水泥墙面，让自然光在一天之中随时间推移刻画空间的几何韵律。材料上选用原木、生铁与粗纺亚麻，营造出安宁、内省的栖居氛围。',
            image: 'https://placehold.co/1200x800/1c1917/d6d3d1?text=Ghost+Order+Interior',
            tags: ['材料美学', '光影雕刻', '现象学住宅']
        },
        {
            id: 2,
            title: '生态拓扑：算法驱动的微气候模块',
            category: 'Spatial Research',
            catSlug: 'research',
            year: '2025',
            summary: '利用计算化设计模拟自然通风与热工效应，重构高密度城市中的微型公共庇护所。',
            description: '本研究深入探讨环境心理学与建筑形态的交互关系。通过Grasshopper参数化脚本，优化建筑表皮的开孔率，使室内空间在无需过度依赖机械空调的前提下，实现高效的自然拔风与温湿度调节。',
            image: 'https://placehold.co/1200x800/1c1917/d6d3d1?text=Eco-Topology+Research',
            tags: ['参数化设计', '环境心理学', '可持续微气候']
        },
        {
            id: 3,
            title: '记忆碎片：混凝土与废弃纤维的对话',
            category: 'Mixed-Media Art',
            catSlug: 'art',
            year: '2024',
            summary: '将建筑拆除废料与回收工业纤维融合，创作一系列反思人与物质异化关系的雕塑装置。',
            description: '装置艺术探索。我们将城市化进程中被抛弃的粗粝混凝土块与柔韧的废弃纤维交织，在坚硬与柔软、永恒与消逝之间寻找平衡点，探讨现代人精神场域中的失落与重构。',
            image: 'https://placehold.co/1200x800/1c1917/d6d3d1?text=Memory+Fragments+Art',
            tags: ['装置艺术', '物质性探索', '循环美学']
        },
        {
            id: 4,
            title: '流体阈限：数字算法生成的公共流线',
            category: 'Computational Design',
            catSlug: 'computational',
            year: '2024',
            summary: '基于 Voronoi 图解与人群步态模拟的商业综合体大堂流线形态优化方案。',
            description: '通过行为数据模拟，分析人流在大型公共空间的聚集、停留与疏散习惯。设计打破了传统的直角网格，采用具流线感的连续曲面引导视线和动线，实现空间效率与视觉美学的统一。',
            image: 'https://placehold.co/1200x800/1c1917/d6d3d1?text=Fluid+Threshold+Computation',
            tags: ['算法流线', '空间逻辑', '行为模拟']
        },
        {
            id: 5,
            title: '静谧之核：禅意茶室与无界庭院',
            category: 'Interior Design',
            catSlug: 'interior',
            year: '2023',
            summary: '模糊室内与室外界限的沉浸式茶室设计，强调触觉反馈与精神冥想。',
            description: '设计旨在喧嚣都市中切出一片静谧真空。通过低矮的水平线条、全景超白玻璃以及黑火山岩铺地，让访客在品茗的同时，能够重新感知风、雨与植物的季节更迭。',
            image: 'https://placehold.co/1200x800/1c1917/d6d3d1?text=The+Silent+Core',
            tags: ['东方当代', '触觉设计', '静谧空间']
        },
        {
            id: 6,
            title: '声景共振：声音折射率的物理装置',
            category: 'Spatial Research',
            catSlug: 'research',
            year: '2023',
            summary: '研究不同空间几何曲率对声波反射与扩散的影响，打造可听觉感知的建筑雕塑。',
            description: '跨学科研究项目，结合声学工程与空间形态学。通过错落的穿孔铝板与双曲面陶土单元，实现特定频段噪音的吸收与扩散，在视觉上展现声音的波动轨迹。',
            image: 'https://placehold.co/1200x800/1c1917/d6d3d1?text=Acoustic+Resonance',
            tags: ['声学空间', '形态学', '跨学科探索']
        }
    ]"
    :class="darkMode ? 'bg-stone-950 text-stone-100' : 'bg-stone-50 text-stone-900'"
    class="transition-colors duration-500 selection:bg-stone-700 selection:text-white">

    <header class="fixed top-0 left-0 w-full z-40 backdrop-blur-md border-b"
            :class="darkMode ? 'bg-stone-950/80 border-stone-800/80' : 'bg-stone-50/80 border-stone-200/80'">
        <div class="max-w-7xl mx-auto px-6 h-20 flex items-center justify-between">
            <a href="#" class="serif-title text-xl tracking-wider font-semibold">
                KAIROS <span class="text-xs font-sans font-normal opacity-60 tracking-widest ml-2">// STUDIO</span>
            </a>

            <!-- Desktop Nav -->
            <nav class="hidden md:flex items-center space-x-10 text-sm tracking-widest uppercase font-medium">
                <a href="#projects" class="hover:opacity-50 transition-opacity">作品 (Works)</a>
                <a href="#philosophy" class="hover:opacity-50 transition-opacity">哲学 (Philosophy)</a>
                <a href="#about" class="hover:opacity-50 transition-opacity">关于 (About)</a>
                <a href="#contact" class="hover:opacity-50 transition-opacity">联系 (Contact)</a>
            </nav>

            <div class="flex items-center space-x-4">
                <!-- Theme Toggle Button -->
                <button @click="darkMode = !darkMode" class="p-2 rounded-full border border-current opacity-70 hover:opacity-100 transition-opacity" aria-label="切换主题">
                    <svg x-show="darkMode" class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path></svg>
                    <svg x-show="!darkMode" class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path></svg>
                </button>

                <!-- Mobile Menu Button -->
                <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden p-2">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path x-show="!mobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 8h16M4 16h16"></path>
                        <path x-show="mobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
        </div>

        <!-- Mobile Nav Dropdown -->
        <div x-show="mobileMenuOpen" x-transition class="md:hidden border-b px-6 py-6 space-y-4" :class="darkMode ? 'bg-stone-900 border-stone-800' : 'bg-white border-stone-200'">
            <a @click="mobileMenuOpen = false" href="#projects" class="block text-sm uppercase tracking-widest">作品 (Works)</a>
            <a @click="mobileMenuOpen = false" href="#philosophy" class="block text-sm uppercase tracking-widest">哲学 (Philosophy)</a>
            <a @click="mobileMenuOpen = false" href="#about" class="block text-sm uppercase tracking-widest">关于 (About)</a>
            <a @click="mobileMenuOpen = false" href="#contact" class="block text-sm uppercase tracking-widest">联系 (Contact)</a>
        </div>
    </header>

    <section class="min-h-screen flex flex-col justify-center px-6 pt-24 pb-16 max-w-7xl mx-auto">
        <div class="space-y-6">
            <div class="inline-block text-xs uppercase tracking-[0.3em] opacity-60 border-b pb-1" :class="darkMode ? 'border-stone-800' : 'border-stone-200'">
                Spatial Research & Interior Architecture Studio
            </div>
            <h1 class="serif-title text-5xl sm:text-7xl lg:text-8xl font-normal leading-[1.1] tracking-tight max-w-5xl">
                空间作为行为的镜子，<br><span class="italic font-light">感知</span>作为建筑的尺度。
            </h1>
            <p class="text-base sm:text-lg opacity-70 max-w-2xl font-light leading-relaxed pt-4">
                我们致力于探索环境心理学、计算化设计与材料本体之间的深刻联结，在虚实、光影与克制的体块中构筑当代栖居的诗意场域。
            </p>
        </div>
        <div class="mt-16 flex items-center space-x-6 text-sm uppercase tracking-widest">
            <a href="#projects" class="group flex items-center space-x-3 opacity-90 hover:opacity-100 transition-opacity">
                <span>浏览精选作品</span>
                <span class="inline-block transform group-hover:translate-x-1 transition-transform">→</span>
            </a>
            <span class="opacity-30">/</span>
            <span class="opacity-50">基于现象学与极简主义</span>
        </div>
    </section>

    <section id="projects" class="py-24 px-6 max-w-7xl mx-auto border-t" :class="darkMode ? 'border-stone-900' : 'border-stone-200'">
        <div class="flex flex-col md:flex-row md:items-end justify-between mb-16 space-y-6 md:space-y-0">
            <div>
                <span class="text-xs uppercase tracking-[0.3em] opacity-50 block mb-2">Selected Portfolio</span>
                <h2 class="serif-title text-4xl sm:text-5xl font-normal">精选实践与研究</h2>
            </div>

            <!-- Filter Buttons -->
            <div class="flex flex-wrap gap-2 text-xs uppercase tracking-wider">
                <button @click="activeFilter = 'all'" 
                        :class="activeFilter === 'all' ? (darkMode ? 'bg-stone-100 text-stone-950' : 'bg-stone-900 text-stone-100') : (darkMode ? 'border-stone-800 hover:border-stone-600' : 'border-stone-300 hover:border-stone-500')"
                        class="px-4 py-2 border rounded-full transition-all">
                    全部 (All)
                </button>
                <button @click="activeFilter = 'interior'" 
                        :class="activeFilter === 'interior' ? (darkMode ? 'bg-stone-100 text-stone-950' : 'bg-stone-900 text-stone-100') : (darkMode ? 'border-stone-800 hover:border-stone-600' : 'border-stone-300 hover:border-stone-500')"
                        class="px-4 py-2 border rounded-full transition-all">
                    室内设计 (Interior)
                </button>
                <button @click="activeFilter = 'research'" 
                        :class="activeFilter === 'research' ? (darkMode ? 'bg-stone-100 text-stone-950' : 'bg-stone-900 text-stone-100') : (darkMode ? 'border-stone-800 hover:border-stone-600' : 'border-stone-300 hover:border-stone-500')"
                        class="px-4 py-2 border rounded-full transition-all">
                    空间研究 (Research)
                </button>
                <button @click="activeFilter = 'art'" 
                        :class="activeFilter === 'art' ? (darkMode ? 'bg-stone-100 text-stone-950' : 'bg-stone-900 text-stone-100') : (darkMode ? 'border-stone-800 hover:border-stone-600' : 'border-stone-300 hover:border-stone-500')"
                        class="px-4 py-2 border rounded-full transition-all">
                    混合媒介艺术 (Art)
                </button>
                <button @click="activeFilter = 'computational'" 
                        :class="activeFilter === 'computational' ? (darkMode ? 'bg-stone-100 text-stone-950' : 'bg-stone-900 text-stone-100') : (darkMode ? 'border-stone-800 hover:border-stone-600' : 'border-stone-300 hover:border-stone-500')"
                        class="px-4 py-2 border rounded-full transition-all">
                    计算化设计 (Computational)
                </button>
            </div>
        </div>

        <!-- Project Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-10">
            <template x-for="project in projects.filter(p => activeFilter === 'all' || p.catSlug === activeFilter)" :key="project.id">
                <div @click="selectedProject = project" class="group cursor-pointer">
                    <div class="overflow-hidden aspect-[4/3] rounded-sm mb-4 relative" :class="darkMode ? 'bg-stone-900' : 'bg-stone-200'">
                        <img :src="project.image" :alt="project.title" class="w-full h-full object-cover grayscale group-hover:grayscale-0 group-hover:scale-105 transition-all duration-700">
                        <div class="absolute top-4 right-4 px-3 py-1 text-xs uppercase tracking-widest backdrop-blur-md rounded-full" :class="darkMode ? 'bg-stone-950/70 text-stone-300' : 'bg-white/70 text-stone-800'">
                            <span x-text="project.year"></span>
                        </div>
                    </div>
                    <div class="flex items-start justify-between">
                        <div>
                            <span class="text-xs uppercase tracking-widest opacity-50 block mb-1" x-text="project.category"></span>
                            <h3 class="serif-title text-2xl group-hover:opacity-75 transition-opacity" x-text="project.title"></h3>
                        </div>
                        <span class="text-lg opacity-40 transform group-hover:translate-x-1 group-hover:-translate-y-1 transition-transform">↗</span>
                    </div>
                    <p class="text-sm opacity-70 mt-2 font-light line-clamp-2" x-text="project.summary"></p>
                </div>
            </template>
        </div>
    </section>

    <section id="philosophy" class="py-24 px-6 border-t" :class="darkMode ? 'border-stone-900 bg-stone-900/40' : 'border-stone-200 bg-stone-100/50'">
        <div class="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
            <div class="lg:col-span-5 space-y-6">
                <span class="text-xs uppercase tracking-[0.3em] opacity-50 block">Design Philosophy</span>
                <h2 class="serif-title text-4xl sm:text-5xl font-normal leading-tight">空间心理学与结构诗学</h2>
                <p class="text-base opacity-75 font-light leading-relaxed">
                    建筑不仅仅是物质的围合，更是人类潜意识的延伸。我们关注空间的边界感、视线交错的阈限，以及光线在粗粝材质上留下的时间痕迹。
                </p>
                <div class="space-y-4 pt-4 border-t" :class="darkMode ? 'border-stone-800' : 'border-stone-300'">
                    <div>
                        <h4 class="text-sm font-medium uppercase tracking-wider">01. 现象学还原 (Phenomenological Reduction)</h4>
                        <p class="text-xs opacity-60 mt-1 font-light">去除多余的符号叠加，回归材料自身的温感、触感与声学反馈。</p>
                    </div>
                    <div>
                        <h4 class="text-sm font-medium uppercase tracking-wider">02. 行为拓扑学 (Behavioral Topology)</h4>
                        <p class="text-xs opacity-60 mt-1 font-light">以人体工学与行为心理为底层逻辑，推演空间流动与停留的秩序。</p>
                    </div>
                    <div>
                        <h4 class="text-sm font-medium uppercase tracking-wider">03. 可持续生态 (Sustainable Craft)</h4>
                        <p class="text-xs opacity-60 mt-1 font-light">融合本地微气候策略，探讨数字算法与传统手工艺的有机结合。</p>
                    </div>
                </div>
            </div>
            <div class="lg:col-span-7">
                <div class="aspect-[16/10] rounded-sm overflow-hidden relative" :class="darkMode ? 'bg-stone-900' : 'bg-stone-200'">
                    <img src="https://placehold.co/1200x800/1c1917/d6d3d1?text=Spatial+Philosophy+Diagram" alt="Philosophy Diagram" class="w-full h-full object-cover grayscale opacity-80">
                    <div class="absolute inset-0 bg-gradient-to-t from-stone-950/60 to-transparent flex items-end p-8">
                        <p class="text-xs uppercase tracking-widest text-stone-300 font-light">// 研究手稿：阈限空间与心理感知模型的交叉分析</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="about" class="py-24 px-6 max-w-7xl mx-auto border-t" :class="darkMode ? 'border-stone-900' : 'border-stone-200'">
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-start">
            <div class="lg:col-span-5">
                <div class="aspect-[3/4] rounded-sm overflow-hidden" :class="darkMode ? 'bg-stone-900' : 'bg-stone-200'">
                    <img src="https://placehold.co/800x1000/1c1917/d6d3d1?text=Designer+Portrait" alt="Architect Portrait" class="w-full h-full object-cover grayscale">
                </div>
            </div>
            <div class="lg:col-span-7 space-y-6">
                <span class="text-xs uppercase tracking-[0.3em] opacity-50 block">About the Researcher</span>
                <h2 class="serif-title text-4xl sm:text-5xl font-normal">关于主创</h2>
                <div class="text-base opacity-80 font-light leading-relaxed space-y-4">
                    <p>
                        毕业于顶尖建筑院校，曾于多伦多及苏黎世建筑事务所参与前沿公共空间与微环境研究。我的实践横跨室内建筑设计、计算化空间形态学与混合媒介雕塑装置。
                    </p>
                    <p>
                        我相信，最理想的设计是在秩序与偶然之间找到完美的平衡点——让理性严谨的逻辑构架包裹感性柔和的居住体验。
                    </p>
                </div>
                <div class="grid grid-cols-2 gap-6 pt-6 border-t" :class="darkMode ? 'border-stone-800' : 'border-stone-300'">
                    <div>
                        <h4 class="text-xs uppercase tracking-widest opacity-50 mb-2">荣誉与奖项</h4>
                        <ul class="text-sm space-y-1 font-light opacity-80">
                            <li>2025 新锐室内建筑师提名</li>
                            <li>2024 Architizer A+ 奖项入围</li>
                            <li>2023 国际空间算法研究展参展</li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="text-xs uppercase tracking-widest opacity-50 mb-2">核心专长</h4>
                        <ul class="text-sm space-y-1 font-light opacity-80">
                            <li>高端住宅与商业空间室内设计</li>
                            <li>环境心理学与微气候优化</li>
                            <li>计算化参数化模型研究</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <footer id="contact" class="py-24 px-6 border-t" :class="darkMode ? 'border-stone-900 bg-stone-900/20' : 'border-stone-200 bg-stone-100/40'">
        <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-12">
            <div class="space-y-6">
                <span class="text-xs uppercase tracking-[0.3em] opacity-50 block">Get in Touch</span>
                <h2 class="serif-title text-4xl sm:text-5xl font-normal">开启新的空间对话。</h2>
                <p class="text-sm opacity-70 font-light max-w-md">
                    无论是关于室内设计委托、学术研究合作，或是观念艺术探讨，随时欢迎通过电邮或社交媒体与我们联系。
                </p>
                <div class="pt-4">
                    <a href="mailto:contact@kairos-studio.arch" class="inline-block text-lg border-b pb-1 font-serif italic hover:opacity-75 transition-opacity" :class="darkMode ? 'border-stone-700' : 'border-stone-400'">
                        contact@kairos-studio.arch
                    </a>
                </div>
            </div>

            <div class="flex flex-col justify-between space-y-8 md:items-end">
                <div class="space-y-4 md:text-right">
                    <span class="text-xs uppercase tracking-[0.3em] opacity-50 block">Social & Networks</span>
                    <div class="flex flex-col md:items-end space-y-2 text-sm uppercase tracking-widest">
                        <a href="#" class="hover:opacity-50 transition-opacity">Instagram // @kairos.spatial</a>
                        <a href="#" class="hover:opacity-50 transition-opacity">LinkedIn // Kairos Studio</a>
                        <a href="#" class="hover:opacity-50 transition-opacity">Behance // Kairos Architecture</a>
                        <a href="#" class="hover:opacity-50 transition-opacity">Substack // Spatial Notes</a>
                    </div>
                </div>
                <div class="text-xs opacity-40 uppercase tracking-widest">
                    © 2026 KAIROS STUDIO. All Rights Reserved.
                </div>
            </div>
        </div>
    </footer>

    <div x-show="selectedProject" 
         x-transition.opacity 
         class="fixed inset-0 z-50 flex items-center justify-center p-4 sm:p-6 bg-black/80 backdrop-blur-sm"
         style="display: none;">
        <div @click.away="selectedProject = null" 
             class="w-full max-w-4xl max-h-[90vh] overflow-y-auto rounded-sm p-6 sm:p-10 relative border"
             :class="darkMode ? 'bg-stone-900 border-stone-800 text-stone-100' : 'bg-white border-stone-200 text-stone-900'">
            
            <button @click="selectedProject = null" class="absolute top-6 right-6 p-2 rounded-full opacity-70 hover:opacity-100 transition-opacity">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
            </button>

            <template x-if="selectedProject">
                <div class="space-y-8">
                    <div>
                        <div class="flex items-center space-x-3 text-xs uppercase tracking-widest opacity-50 mb-2">
                            <span x-text="selectedProject.category"></span>
                            <span>/</span>
                            <span x-text="selectedProject.year"></span>
                        </div>
                        <h2 class="serif-title text-3xl sm:text-4xl" x-text="selectedProject.title"></h2>
                    </div>

                    <div class="aspect-[16/9] rounded-sm overflow-hidden" :class="darkMode ? 'bg-stone-800' : 'bg-stone-200'">
                        <img :src="selectedProject.image" :alt="selectedProject.title" class="w-full h-full object-cover">
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 pt-4 border-t" :class="darkMode ? 'border-stone-800' : 'border-stone-200'">
                        <div class="md:col-span-2 space-y-4">
                            <h3 class="text-xs uppercase tracking-widest opacity-50">项目深度解析 (Project Narrative)</h3>
                            <p class="text-sm sm:text-base font-light leading-relaxed opacity-85" x-text="selectedProject.description"></p>
                        </div>
                        <div class="space-y-4">
                            <h3 class="text-xs uppercase tracking-widest opacity-50">核心关键词 (Tags)</h3>
                            <div class="flex flex-wrap gap-2">
                                <template x-for="tag in selectedProject.tags">
                                    <span class="px-3 py-1 text-xs uppercase tracking-wider rounded-full border" :class="darkMode ? 'border-stone-800 bg-stone-950 text-stone-300' : 'border-stone-200 bg-stone-100 text-stone-700'" x-text="tag"></span>
                                </template>
                            </div>
                        </div>
                    </div>

                    <div class="flex justify-end pt-6 border-t" :class="darkMode ? 'border-stone-800' : 'border-stone-200'">
                        <button @click="selectedProject = null" class="px-6 py-2 border rounded-full text-xs uppercase tracking-widest hover:opacity-75 transition-opacity" :class="darkMode ? 'border-stone-700' : 'border-stone-300'">
                            关闭窗口 (Close)
                        </button>
                    </div>
                </div>
            </template>
        </div>
    </div>

</body>
</html>
