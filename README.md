- 👋 Hi, I’m @mohammadsh123456
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
- 
<!---<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>إدارة المنتجات والأقسام</title>
    <meta name="description" content="تطبيق لإدارة المنتجات والأقسام مع تحويل العملات">
    <link rel="manifest" href="manifest.json">
    <meta name="theme-color" content="#5D5CDE">
    <link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath fill='%235D5CDE' d='M3 3h18v18H3V3zm16 16V5H5v14h14zm-6-3H7v-2h6v2zm4-4H7v-2h10v2zm0-4H7V6h10v2z'/%3E%3C/svg%3E" type="image/svg+xml">
    <link rel="apple-touch-icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Crect width='24' height='24' fill='%235D5CDE' rx='12' ry='12'/%3E%3Cpath fill='white' d='M7 7h10v2H7V7zm0 4h10v2H7v-2zm0 4h6v2H7v-2z'/%3E%3C/svg%3E">
    
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                    }
                }
            }
        }
    </script>
    <style>
        input[type=number]::-webkit-inner-spin-button, 
        input[type=number]::-webkit-outer-spin-button { 
            -webkit-appearance: none; 
            margin: 0; 
        }
        input[type=number] {
            -moz-appearance: textfield;
        }
        
        /* Dark mode styles */
        .dark {
            color-scheme: dark;
        }

        /* Transition for view changes */
        .view-transition {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.3s ease, transform 0.3s ease;
        }
        .view-transition.active {
            opacity: 1;
            transform: translateY(0);
        }
        
        /* Modal animations */
        .modal-overlay {
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        .modal-overlay.active {
            opacity: 1;
        }
        .modal-container {
            transform: translateY(50px);
            opacity: 0;
            transition: transform 0.3s ease, opacity 0.3s ease;
        }
        .modal-container.active {
            transform: translateY(0);
            opacity: 1;
        }
        
        /* Fixed action buttons */
        .fixed-btn {
            position: fixed;
            bottom: 20px;
            left: 20px;
            z-index: 40;
        }
        
        /* Highlight search results */
        .highlight {
            background-color: yellow;
            color: black;
            padding: 0 2px;
            border-radius: 2px;
        }
        
        /* App installation prompt */
        .install-prompt {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #5D5CDE;
            color: white;
            padding: 10px 15px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            display: none;
            z-index: 50;
            animation: slideUp 0.3s forwards;
        }
        
        @keyframes slideUp {
            from {
                transform: translateY(20px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        
        /* Spinning animation for loading */
        @keyframes spin {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }
        .animate-spin {
            animation: spin 1s linear infinite;
        }
    </style>
</head>
<body class="font-sans antialiased">
    <div class="min-h-screen bg-white dark:bg-[#181818] dark:text-white transition-colors duration-300">
        <div class="container mx-auto px-4 py-6">
            <!-- Header with app title and dollar rate -->
            <div class="flex flex-col md:flex-row items-center justify-between mb-4">
                <h1 class="text-3xl font-bold text-primary">إدارة المنتجات</h1>
                
                <div class="flex items-center mt-4 md:mt-0 bg-gray-100 dark:bg-gray-800 p-3 rounded-lg">
                    <label for="dollar-rate" class="ml-2 font-medium">سعر الدولار:</label>
                    <input type="number" id="dollar-rate" class="w-28 p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" value="13000">
                    <span class="mr-2">ل.س</span>
                </div>
            </div>
            
            <!-- Search Bar -->
            <div class="relative mb-6">
                <div class="flex">
                    <div class="relative flex-grow">
                        <input 
                            type="text" 
                            id="search-input" 
                            placeholder="ابحث عن منتج أو قسم..." 
                            class="w-full p-3 pl-10 border border-gray-300 dark:border-gray-600 rounded-lg bg-white dark:bg-gray-700 text-base"
                        >
                        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                            </svg>
                        </div>
                        <button 
                            id="clear-search" 
                            class="absolute inset-y-0 right-0 pr-3 flex items-center text-gray-400 hover:text-gray-600 dark:hover:text-gray-300 hidden"
                        >
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                            </svg>
                        </button>
                    </div>
                    <div class="ml-2">
                        <button id="export-data" class="bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded-lg transition-colors flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-8l-4-4m0 0L8 8m4-4v12" />
                            </svg>
                            تصدير
                        </button>
                    </div>
                    <div class="ml-2">
                        <input type="file" id="import-file" accept=".json" class="hidden">
                        <button id="import-data" class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded-lg transition-colors flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
                            </svg>
                            استيراد
                        </button>
                    </div>
                </div>
                <!-- Search Results Counter -->
                <div id="search-results-count" class="text-sm text-gray-500 mt-1 hidden">
                    لا توجد نتائج بحث
                </div>
            </div>
            
            <!-- Navigation / Breadcrumbs -->
            <div class="flex items-center mb-6 text-gray-600 dark:text-gray-400">
                <button id="home-btn" class="flex items-center hover:text-primary transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                        <path d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" />
                    </svg>
                    الرئيسية
                </button>
                <span id="category-breadcrumb" class="hidden">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mx-2" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
                    </svg>
                    <span id="current-category-name" class="flex items-center">
                        <span id="category-name-display"></span>
                        <button id="edit-category-name-btn" class="mr-2 text-gray-500 hover:text-primary">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
                            </svg>
                        </button>
                    </span>
                </span>
            </div>
            
            <!-- Save Data Button (Top) -->
            <div class="flex justify-end mb-4">
                <button id="save-data-btn" class="bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded-lg transition-colors flex items-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                        <path d="M7.707 10.293a1 1 0 10-1.414 1.414l3 3a1 1 0 001.414 0l3-3a1 1 0 00-1.414-1.414L11 11.586V6h5a2 2 0 012 2v7a2 2 0 01-2 2H4a2 2 0 01-2-2V8a2 2 0 012-2h5v5.586l-1.293-1.293zM9 4a1 1 0 012 0v2H9V4z" />
                    </svg>
                    حفظ البيانات
                </button>
            </div>
            
            <!-- Main Content Views -->
            <div id="views-container">
                <!-- Categories View (Home) -->
                <div id="categories-view" class="view-transition active">
                    <!-- Categories List -->
                    <div id="categories-list" class="grid grid-cols-2 gap-4">
                        <div class="text-center text-gray-500 dark:text-gray-400 p-8 col-span-full" id="no-categories">
                            لا توجد أقسام. أضف قسماً جديداً للبدء.
                        </div>
                        <!-- Categories will be dynamically added here -->
                    </div>
                </div>
                
                <!-- Category Details View (Products) -->
                <div id="category-details-view" class="view-transition hidden">
                    <!-- Products List -->
                    <div id="products-list" class="overflow-x-auto">
                        <div class="text-center text-gray-500 dark:text-gray-400 p-8" id="no-products">
                            لا توجد منتجات في هذا القسم. أضف منتجاً جديداً للبدء.
                        </div>
                        <table class="w-full border-collapse hidden" id="products-table">
                            <thead>
                                <tr class="bg-gray-200 dark:bg-gray-700">
                                    <th class="p-3 text-right">المنتج</th>
                                    <th class="p-3 text-right">السعر (دولار)</th>
                                    <th class="p-3 text-right">السعر (ل.س)</th>
                                    <th class="p-3 text-center">إجراءات</th>
                                </tr>
                            </thead>
                            <tbody id="products-body"></tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Install Prompt -->
    <div id="install-prompt" class="install-prompt">
        <div class="flex items-center justify-between">
            <div class="flex items-center">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
                </svg>
                <span>تثبيت التطبيق على جهازك</span>
            </div>
            <div class="flex">
                <button id="install-later" class="text-white/80 hover:text-white ml-2">لاحقاً</button>
                <button id="install-now" class="bg-white text-primary px-3 py-1 rounded-lg font-medium">تثبيت</button>
            </div>
        </div>
    </div>
    
    <!-- Fixed Action Button -->
    <div id="add-button" class="fixed-btn">
        <button id="add-category-btn" class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-lg shadow-lg flex items-center mb-2 hidden">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
            </svg>
            إضافة قسم
        </button>
        <button id="add-product-btn" class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg shadow-lg flex items-center hidden">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
            </svg>
            إضافة منتج
        </button>
    </div>
    
    <!-- Modals -->
    <!-- Add Category Modal -->
    <div id="add-category-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-md mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">إضافة قسم جديد</h3>
                </div>
                <div class="p-6">
                    <div class="mb-4">
                        <label for="modal-category-name" class="block mb-2 font-medium">اسم القسم</label>
                        <input type="text" id="modal-category-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم القسم">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-category-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-category-bg-color" class="w-full h-10 rounded cursor-pointer" value="#5D5CDE">
                        </div>
                        <div>
                            <label for="modal-category-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-category-text-color" class="w-full h-10 rounded cursor-pointer" value="#FFFFFF">
                        </div>
                    </div>
                    <div class="flex justify-end space-x-2 space-x-reverse">
                        <button id="modal-cancel-category" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                            إلغاء
                        </button>
                        <button id="modal-save-category" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                            حفظ
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Add Product Modal -->
    <div id="add-product-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-lg mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">إضافة منتج جديد</h3>
                </div>
                <div class="p-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-product-name" class="block mb-2 font-medium">اسم المنتج</label>
                            <input type="text" id="modal-product-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم المنتج">
                        </div>
                        <div>
                            <label for="modal-product-price" class="block mb-2 font-medium">السعر بالدولار</label>
                            <input type="number" id="modal-product-price" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="السعر">
                        </div>
                    </div>
                    <div class="mb-4">
                        <label for="modal-product-price-syp" class="block mb-2 font-medium">السعر بالليرة السورية</label>
                        <input type="text" id="modal-product-price-syp" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-gray-100 dark:bg-gray-600 text-base" readonly placeholder="يحسب تلقائياً">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-product-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-product-bg-color" class="w-full h-10 rounded cursor-pointer" value="#FFFFFF">
                        </div>
                        <div>
                            <label for="modal-product-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-product-text-color" class="w-full h-10 rounded cursor-pointer" value="#000000">
                        </div>
                    </div>
                    <div class="flex justify-end space-x-2 space-x-reverse">
                        <button id="modal-cancel-product" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                            إلغاء
                        </button>
                        <button id="modal-save-product" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                            حفظ
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Edit Category Modal -->
    <div id="edit-category-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-md mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">تعديل القسم</h3>
                </div>
                <div class="p-6">
                    <div class="mb-4">
                        <label for="modal-edit-category-name" class="block mb-2 font-medium">اسم القسم</label>
                        <input type="text" id="modal-edit-category-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم القسم الجديد">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-edit-category-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-edit-category-bg-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                        <div>
                            <label for="modal-edit-category-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-edit-category-text-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                    </div>
                    <div class="flex justify-between">
                        <button id="modal-delete-category" class="px-4 py-2 bg-red-500 hover:bg-red-600 text-white rounded transition-colors">
                            حذف القسم
                        </button>
                        <div class="flex space-x-2 space-x-reverse">
                            <button id="modal-cancel-edit-category" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                                إلغاء
                            </button>
                            <button id="modal-save-edit-category" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                                حفظ
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Edit Product Modal -->
    <div id="edit-product-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-lg mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">تعديل المنتج</h3>
                </div>
                <div class="p-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-edit-product-name" class="block mb-2 font-medium">اسم المنتج</label>
                            <input type="text" id="modal-edit-product-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم المنتج">
                        </div>
                        <div>
                            <label for="modal-edit-product-price" class="block mb-2 font-medium">السعر بالدولار</label>
                            <input type="number" id="modal-edit-product-price" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="السعر">
                        </div>
                    </div>
                    <div class="mb-4">
                        <label for="modal-edit-product-price-syp" class="block mb-2 font-medium">السعر بالليرة السورية</label>
                        <input type="text" id="modal-edit-product-price-syp" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-gray-100 dark:bg-gray-600 text-base" readonly placeholder="يحسب تلقائياً">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-edit-product-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-edit-product-bg-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                        <div>
                            <label for="modal-edit-product-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-edit-product-text-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                    </div>
                    <div class="flex justify-between">
                        <button id="modal-delete-product" class="px-4 py-2 bg-red-500 hover:bg-red-600 text-white rounded transition-colors">
                            حذف المنتج
                        </button>
                        <div class="flex space-x-2 space-x-reverse">
                            <button id="modal-cancel-edit-product" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                                إلغاء
                            </button>
                            <button id="modal-save-edit-product" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                                حفظ
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="app.js"></script>
    <script>
        // Register service worker for offline functionality
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                navigator.serviceWorker.register('service-worker.js').then(registration => {
                    console.log('Service worker registered:', registration);
                }).catch(error => {
                    console.log('Service worker registration failed:', error);
                });
            });
        }
        
        // PWA Install functionality
        let deferredPrompt;
        const installPrompt = document.getElementById('install-prompt');
        const installNowBtn = document.getElementById('install-now');
        const installLaterBtn = document.getElementById('install-later');
        
        window.addEventListener('beforeinstallprompt', (e) => {
            // Prevent Chrome 67 and earlier from automatically showing the prompt
            e.preventDefault();
            // Stash the event so it can be triggered later
            deferredPrompt = e;
            // Show the install button
            installPrompt.style.display = 'block';
        });
        
        installNowBtn.addEventListener('click', () => {
            // Hide the app provided install promotion
            installPrompt.style.display = 'none';
            // Show the install prompt
            deferredPrompt.prompt();
            // Wait for the user to respond to the prompt
            deferredPrompt.userChoice.then((choiceResult) => {
                if (choiceResult.outcome === 'accepted') {
                    console.log('User accepted the install prompt');
                } else {
                    console.log('User dismissed the install prompt');
                }
                deferredPrompt = null;
            });
        });
        
        installLaterBtn.addEventListener('click', () => {
            installPrompt.style.display = 'none';
        });
    </script>
</body>
</html>

mohammadsh123456/mohammadsh123456 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
---<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>إدارة المنتجات والأقسام</title>
    <meta name="description" content="تطبيق لإدارة المنتجات والأقسام مع تحويل العملات">
    <link rel="manifest" href="manifest.json">
    <meta name="theme-color" content="#5D5CDE">
    <link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath fill='%235D5CDE' d='M3 3h18v18H3V3zm16 16V5H5v14h14zm-6-3H7v-2h6v2zm4-4H7v-2h10v2zm0-4H7V6h10v2z'/%3E%3C/svg%3E" type="image/svg+xml">
    <link rel="apple-touch-icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Crect width='24' height='24' fill='%235D5CDE' rx='12' ry='12'/%3E%3Cpath fill='white' d='M7 7h10v2H7V7zm0 4h10v2H7v-2zm0 4h6v2H7v-2z'/%3E%3C/svg%3E">
    
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                    }
                }
            }
        }
    </script>
    <style>
        input[type=number]::-webkit-inner-spin-button, 
        input[type=number]::-webkit-outer-spin-button { 
            -webkit-appearance: none; 
            margin: 0; 
        }
        input[type=number] {
            -moz-appearance: textfield;
        }
        
        /* Dark mode styles */
        .dark {
            color-scheme: dark;
        }

        /* Transition for view changes */
        .view-transition {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.3s ease, transform 0.3s ease;
        }
        .view-transition.active {
            opacity: 1;
            transform: translateY(0);
        }
        
        /* Modal animations */
        .modal-overlay {
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        .modal-overlay.active {
            opacity: 1;
        }
        .modal-container {
            transform: translateY(50px);
            opacity: 0;
            transition: transform 0.3s ease, opacity 0.3s ease;
        }
        .modal-container.active {
            transform: translateY(0);
            opacity: 1;
        }
        
        /* Fixed action buttons */
        .fixed-btn {
            position: fixed;
            bottom: 20px;
            left: 20px;
            z-index: 40;
        }
        
        /* Highlight search results */
        .highlight {
            background-color: yellow;
            color: black;
            padding: 0 2px;
            border-radius: 2px;
        }
        
        /* App installation prompt */
        .install-prompt {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #5D5CDE;
            color: white;
            padding: 10px 15px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            display: none;
            z-index: 50;
            animation: slideUp 0.3s forwards;
        }
        
        @keyframes slideUp {
            from {
                transform: translateY(20px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        
        /* Spinning animation for loading */
        @keyframes spin {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }
        .animate-spin {
            animation: spin 1s linear infinite;
        }
    </style>
</head>
<body class="font-sans antialiased">
    <div class="min-h-screen bg-white dark:bg-[#181818] dark:text-white transition-colors duration-300">
        <div class="container mx-auto px-4 py-6">
            <!-- Header with app title and dollar rate -->
            <div class="flex flex-col md:flex-row items-center justify-between mb-4">
                <h1 class="text-3xl font-bold text-primary">إدارة المنتجات</h1>
                
                <div class="flex items-center mt-4 md:mt-0 bg-gray-100 dark:bg-gray-800 p-3 rounded-lg">
                    <label for="dollar-rate" class="ml-2 font-medium">سعر الدولار:</label>
                    <input type="number" id="dollar-rate" class="w-28 p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" value="13000">
                    <span class="mr-2">ل.س</span>
                </div>
            </div>
            
            <!-- Search Bar -->
            <div class="relative mb-6">
                <div class="flex">
                    <div class="relative flex-grow">
                        <input 
                            type="text" 
                            id="search-input" 
                            placeholder="ابحث عن منتج أو قسم..." 
                            class="w-full p-3 pl-10 border border-gray-300 dark:border-gray-600 rounded-lg bg-white dark:bg-gray-700 text-base"
                        >
                        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                            </svg>
                        </div>
                        <button 
                            id="clear-search" 
                            class="absolute inset-y-0 right-0 pr-3 flex items-center text-gray-400 hover:text-gray-600 dark:hover:text-gray-300 hidden"
                        >
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                            </svg>
                        </button>
                    </div>
                    <div class="ml-2">
                        <button id="export-data" class="bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded-lg transition-colors flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-8l-4-4m0 0L8 8m4-4v12" />
                            </svg>
                            تصدير
                        </button>
                    </div>
                    <div class="ml-2">
                        <input type="file" id="import-file" accept=".json" class="hidden">
                        <button id="import-data" class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded-lg transition-colors flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
                            </svg>
                            استيراد
                        </button>
                    </div>
                </div>
                <!-- Search Results Counter -->
                <div id="search-results-count" class="text-sm text-gray-500 mt-1 hidden">
                    لا توجد نتائج بحث
                </div>
            </div>
            
            <!-- Navigation / Breadcrumbs -->
            <div class="flex items-center mb-6 text-gray-600 dark:text-gray-400">
                <button id="home-btn" class="flex items-center hover:text-primary transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                        <path d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" />
                    </svg>
                    الرئيسية
                </button>
                <span id="category-breadcrumb" class="hidden">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mx-2" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
                    </svg>
                    <span id="current-category-name" class="flex items-center">
                        <span id="category-name-display"></span>
                        <button id="edit-category-name-btn" class="mr-2 text-gray-500 hover:text-primary">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
                            </svg>
                        </button>
                    </span>
                </span>
            </div>
            
            <!-- Save Data Button (Top) -->
            <div class="flex justify-end mb-4">
                <button id="save-data-btn" class="bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded-lg transition-colors flex items-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                        <path d="M7.707 10.293a1 1 0 10-1.414 1.414l3 3a1 1 0 001.414 0l3-3a1 1 0 00-1.414-1.414L11 11.586V6h5a2 2 0 012 2v7a2 2 0 01-2 2H4a2 2 0 01-2-2V8a2 2 0 012-2h5v5.586l-1.293-1.293zM9 4a1 1 0 012 0v2H9V4z" />
                    </svg>
                    حفظ البيانات
                </button>
            </div>
            
            <!-- Main Content Views -->
            <div id="views-container">
                <!-- Categories View (Home) -->
                <div id="categories-view" class="view-transition active">
                    <!-- Categories List -->
                    <div id="categories-list" class="grid grid-cols-2 gap-4">
                        <div class="text-center text-gray-500 dark:text-gray-400 p-8 col-span-full" id="no-categories">
                            لا توجد أقسام. أضف قسماً جديداً للبدء.
                        </div>
                        <!-- Categories will be dynamically added here -->
                    </div>
                </div>
                
                <!-- Category Details View (Products) -->
                <div id="category-details-view" class="view-transition hidden">
                    <!-- Products List -->
                    <div id="products-list" class="overflow-x-auto">
                        <div class="text-center text-gray-500 dark:text-gray-400 p-8" id="no-products">
                            لا توجد منتجات في هذا القسم. أضف منتجاً جديداً للبدء.
                        </div>
                        <table class="w-full border-collapse hidden" id="products-table">
                            <thead>
                                <tr class="bg-gray-200 dark:bg-gray-700">
                                    <th class="p-3 text-right">المنتج</th>
                                    <th class="p-3 text-right">السعر (دولار)</th>
                                    <th class="p-3 text-right">السعر (ل.س)</th>
                                    <th class="p-3 text-center">إجراءات</th>
                                </tr>
                            </thead>
                            <tbody id="products-body"></tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Install Prompt -->
    <div id="install-prompt" class="install-prompt">
        <div class="flex items-center justify-between">
            <div class="flex items-center">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
                </svg>
                <span>تثبيت التطبيق على جهازك</span>
            </div>
            <div class="flex">
                <button id="install-later" class="text-white/80 hover:text-white ml-2">لاحقاً</button>
                <button id="install-now" class="bg-white text-primary px-3 py-1 rounded-lg font-medium">تثبيت</button>
            </div>
        </div>
    </div>
    
    <!-- Fixed Action Button -->
    <div id="add-button" class="fixed-btn">
        <button id="add-category-btn" class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-lg shadow-lg flex items-center mb-2 hidden">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
            </svg>
            إضافة قسم
        </button>
        <button id="add-product-btn" class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg shadow-lg flex items-center hidden">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
            </svg>
            إضافة منتج
        </button>
    </div>
    
    <!-- Modals -->
    <!-- Add Category Modal -->
    <div id="add-category-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-md mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">إضافة قسم جديد</h3>
                </div>
                <div class="p-6">
                    <div class="mb-4">
                        <label for="modal-category-name" class="block mb-2 font-medium">اسم القسم</label>
                        <input type="text" id="modal-category-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم القسم">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-category-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-category-bg-color" class="w-full h-10 rounded cursor-pointer" value="#5D5CDE">
                        </div>
                        <div>
                            <label for="modal-category-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-category-text-color" class="w-full h-10 rounded cursor-pointer" value="#FFFFFF">
                        </div>
                    </div>
                    <div class="flex justify-end space-x-2 space-x-reverse">
                        <button id="modal-cancel-category" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                            إلغاء
                        </button>
                        <button id="modal-save-category" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                            حفظ
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Add Product Modal -->
    <div id="add-product-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-lg mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">إضافة منتج جديد</h3>
                </div>
                <div class="p-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-product-name" class="block mb-2 font-medium">اسم المنتج</label>
                            <input type="text" id="modal-product-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم المنتج">
                        </div>
                        <div>
                            <label for="modal-product-price" class="block mb-2 font-medium">السعر بالدولار</label>
                            <input type="number" id="modal-product-price" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="السعر">
                        </div>
                    </div>
                    <div class="mb-4">
                        <label for="modal-product-price-syp" class="block mb-2 font-medium">السعر بالليرة السورية</label>
                        <input type="text" id="modal-product-price-syp" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-gray-100 dark:bg-gray-600 text-base" readonly placeholder="يحسب تلقائياً">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-product-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-product-bg-color" class="w-full h-10 rounded cursor-pointer" value="#FFFFFF">
                        </div>
                        <div>
                            <label for="modal-product-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-product-text-color" class="w-full h-10 rounded cursor-pointer" value="#000000">
                        </div>
                    </div>
                    <div class="flex justify-end space-x-2 space-x-reverse">
                        <button id="modal-cancel-product" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                            إلغاء
                        </button>
                        <button id="modal-save-product" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                            حفظ
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Edit Category Modal -->
    <div id="edit-category-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-md mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">تعديل القسم</h3>
                </div>
                <div class="p-6">
                    <div class="mb-4">
                        <label for="modal-edit-category-name" class="block mb-2 font-medium">اسم القسم</label>
                        <input type="text" id="modal-edit-category-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم القسم الجديد">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-edit-category-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-edit-category-bg-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                        <div>
                            <label for="modal-edit-category-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-edit-category-text-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                    </div>
                    <div class="flex justify-between">
                        <button id="modal-delete-category" class="px-4 py-2 bg-red-500 hover:bg-red-600 text-white rounded transition-colors">
                            حذف القسم
                        </button>
                        <div class="flex space-x-2 space-x-reverse">
                            <button id="modal-cancel-edit-category" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                                إلغاء
                            </button>
                            <button id="modal-save-edit-category" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                                حفظ
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Edit Product Modal -->
    <div id="edit-product-modal" class="fixed inset-0 z-50 overflow-auto hidden">
        <div class="modal-overlay fixed inset-0 bg-black bg-opacity-50"></div>
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="modal-container bg-white dark:bg-gray-800 w-full max-w-lg mx-auto rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-4 bg-primary text-white">
                    <h3 class="text-lg font-bold">تعديل المنتج</h3>
                </div>
                <div class="p-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-edit-product-name" class="block mb-2 font-medium">اسم المنتج</label>
                            <input type="text" id="modal-edit-product-name" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="أدخل اسم المنتج">
                        </div>
                        <div>
                            <label for="modal-edit-product-price" class="block mb-2 font-medium">السعر بالدولار</label>
                            <input type="number" id="modal-edit-product-price" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700 text-base" placeholder="السعر">
                        </div>
                    </div>
                    <div class="mb-4">
                        <label for="modal-edit-product-price-syp" class="block mb-2 font-medium">السعر بالليرة السورية</label>
                        <input type="text" id="modal-edit-product-price-syp" class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-gray-100 dark:bg-gray-600 text-base" readonly placeholder="يحسب تلقائياً">
                    </div>
                    <div class="grid grid-cols-2 gap-4 mb-4">
                        <div>
                            <label for="modal-edit-product-bg-color" class="block mb-2 font-medium">لون الخلفية</label>
                            <input type="color" id="modal-edit-product-bg-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                        <div>
                            <label for="modal-edit-product-text-color" class="block mb-2 font-medium">لون النص</label>
                            <input type="color" id="modal-edit-product-text-color" class="w-full h-10 rounded cursor-pointer">
                        </div>
                    </div>
                    <div class="flex justify-between">
                        <button id="modal-delete-product" class="px-4 py-2 bg-red-500 hover:bg-red-600 text-white rounded transition-colors">
                            حذف المنتج
                        </button>
                        <div class="flex space-x-2 space-x-reverse">
                            <button id="modal-cancel-edit-product" class="px-4 py-2 bg-gray-300 dark:bg-gray-600 text-gray-800 dark:text-white rounded hover:bg-gray-400 dark:hover:bg-gray-500 transition-colors">
                                إلغاء
                            </button>
                            <button id="modal-save-edit-product" class="px-4 py-2 bg-primary hover:bg-primary/80 text-white rounded transition-colors">
                                حفظ
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="app.js"></script>
    <script>
        // Register service worker for offline functionality
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                navigator.serviceWorker.register('service-worker.js').then(registration => {
                    console.log('Service worker registered:', registration);
                }).catch(error => {
                    console.log('Service worker registration failed:', error);
                });
            });
        }
        
        // PWA Install functionality
        let deferredPrompt;
        const installPrompt = document.getElementById('install-prompt');
        const installNowBtn = document.getElementById('install-now');
        const installLaterBtn = document.getElementById('install-later');
        
        window.addEventListener('beforeinstallprompt', (e) => {
            // Prevent Chrome 67 and earlier from automatically showing the prompt
            e.preventDefault();
            // Stash the event so it can be triggered later
            deferredPrompt = e;
            // Show the install button
            installPrompt.style.display = 'block';
        });
        
        installNowBtn.addEventListener('click', () => {
            // Hide the app provided install promotion
            installPrompt.style.display = 'none';
            // Show the install prompt
            deferredPrompt.prompt();
            // Wait for the user to respond to the prompt
            deferredPrompt.userChoice.then((choiceResult) => {
                if (choiceResult.outcome === 'accepted') {
                    console.log('User accepted the install prompt');
                } else {
                    console.log('User dismissed the install prompt');
                }
                deferredPrompt = null;
            });
        });
        
        installLaterBtn.addEventListener('click', () => {
            installPrompt.style.display = 'none';
        });
    </script>
</body>
</html>

