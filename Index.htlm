<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5, user-scalable=yes" />
    <title>Todo List App</title>

    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />

    <!-- Google Font -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet" />

    <style>
        /* ============================================
                   CSS VARIABLES & THEMING
                   ============================================ */
        :root {
            --bg-primary: #f0f2f5;
            --bg-secondary: #ffffff;
            --bg-input: #f0f2f5;
            --text-primary: #1a1a2e;
            --text-secondary: #6b7280;
            --accent: #6c63ff;
            --accent-hover: #5a52d5;
            --accent-light: #e8e6ff;
            --success: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.06);
            --shadow-md: 0 4px 20px rgba(0, 0, 0, 0.08);
            --shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.12);
            --border-radius-sm: 8px;
            --border-radius-md: 12px;
            --border-radius-lg: 16px;
            --border-radius-xl: 24px;
            --transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            --font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }

        [data-theme="dark"] {
            --bg-primary: #0f0f1a;
            --bg-secondary: #1a1a2e;
            --bg-input: #252540;
            --text-primary: #f0f0f5;
            --text-secondary: #a0a0b8;
            --accent-light: #2a2555;
            --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.3);
            --shadow-md: 0 4px 20px rgba(0, 0, 0, 0.4);
            --shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.5);
        }

        /* ============================================
                   RESET & BASE
                   ============================================ */
        *,
        *::before,
        *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            font-size: 16px;
            -webkit-text-size-adjust: 100%;
        }

        body {
            font-family: var(--font-family);
            background: var(--bg-primary);
            color: var(--text-primary);
            transition: background 0.4s, color 0.4s;
            min-height: 100vh;
            min-height: 100dvh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 16px;
            line-height: 1.5;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* ============================================
                   APP CONTAINER
                   ============================================ */
        .app-container {
            max-width: 640px;
            width: 100%;
            background: var(--bg-secondary);
            border-radius: var(--border-radius-xl);
            box-shadow: var(--shadow-lg);
            padding: clamp(20px, 5vw, 40px);
            transition: background 0.4s, box-shadow 0.4s;
            margin: 0 auto;
        }

        /* ============================================
                   HEADER
                   ============================================ */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: clamp(20px, 4vw, 32px);
            gap: 12px;
            flex-wrap: wrap;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .header h1 {
            font-size: clamp(1.5rem, 4vw, 2rem);
            font-weight: 700;
            color: var(--text-primary);
            letter-spacing: -0.5px;
        }

        .header h1 span {
            color: var(--accent);
        }

        .header-emoji {
            font-size: clamp(1.5rem, 3vw, 2rem);
        }

        .header-controls {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        #theme-toggle {
            background: var(--bg-input);
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            color: var(--text-primary);
            transition: all var(--transition);
            padding: 8px 12px;
            border-radius: var(--border-radius-sm);
            width: 44px;
            height: 44px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        #theme-toggle:hover {
            transform: rotate(20deg);
            background: var(--accent-light);
        }

        #theme-toggle:active {
            transform: scale(0.92);
        }

        /* ============================================
                   STATS
                   ============================================ */
        .stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 8px;
            background: var(--bg-primary);
            padding: clamp(10px, 2vw, 14px);
            border-radius: var(--border-radius-md);
            margin-bottom: clamp(16px, 3vw, 24px);
            transition: background 0.4s;
        }

        .stat-item {
            text-align: center;
            font-size: clamp(0.75rem, 1.5vw, 0.9rem);
            font-weight: 500;
            color: var(--text-secondary);
        }

        .stat-item .count {
            display: block;
            font-size: clamp(1.2rem, 2.5vw, 1.5rem);
            font-weight: 700;
            color: var(--accent);
            margin-top: 2px;
        }

        .stat-item .count.completed-count {
            color: var(--success);
        }

        .stat-item .count.pending-count {
            color: var(--warning);
        }

        /* ============================================
                   INPUT SECTION
                   ============================================ */
        .input-section {
            display: flex;
            gap: 10px;
            margin-bottom: clamp(16px, 3vw, 24px);
        }

        .input-wrapper {
            flex: 1;
            position: relative;
        }

        .input-wrapper i {
            position: absolute;
            left: 14px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-secondary);
            font-size: 0.9rem;
            opacity: 0.6;
        }

        .input-section input {
            width: 100%;
            padding: clamp(12px, 2vw, 14px) clamp(12px, 2vw, 14px) clamp(12px, 2vw, 14px) 42px;
            border: 2px solid var(--bg-input);
            border-radius: var(--border-radius-md);
            background: var(--bg-input);
            color: var(--text-primary);
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            transition: all var(--transition);
            font-family: inherit;
            -webkit-appearance: none;
            appearance: none;
        }

        .input-section input:focus {
            outline: none;
            border-color: var(--accent);
            background: var(--bg-secondary);
            box-shadow: 0 0 0 4px rgba(108, 99, 255, 0.1);
        }

        .input-section input::placeholder {
            color: var(--text-secondary);
            opacity: 0.7;
        }

        .input-section button {
            padding: clamp(12px, 2vw, 14px) clamp(16px, 3vw, 24px);
            background: var(--accent);
            color: #fff;
            border: none;
            border-radius: var(--border-radius-md);
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            font-weight: 600;
            cursor: pointer;
            transition: all var(--transition);
            white-space: nowrap;
            font-family: inherit;
            display: flex;
            align-items: center;
            gap: 6px;
            min-height: 50px;
            -webkit-tap-highlight-color: transparent;
        }

        .input-section button:hover {
            background: var(--accent-hover);
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(108, 99, 255, 0.3);
        }

        .input-section button:active {
            transform: scale(0.96);
        }

        .input-section button i {
            font-size: clamp(0.8rem, 1.2vw, 1rem);
        }

        /* ============================================
                   FILTER BUTTONS
                   ============================================ */
        .filters {
            display: flex;
            gap: 6px;
            margin-bottom: clamp(16px, 3vw, 24px);
            flex-wrap: wrap;
            justify-content: center;
        }

        .filter-btn {
            padding: clamp(6px, 1vw, 8px) clamp(14px, 2.5vw, 20px);
            border: 2px solid transparent;
            background: var(--bg-input);
            color: var(--text-secondary);
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            transition: all var(--transition);
            font-size: clamp(0.75rem, 1.2vw, 0.85rem);
            font-family: inherit;
            -webkit-tap-highlight-color: transparent;
            flex: 0 1 auto;
            min-height: 38px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .filter-btn.active,
        .filter-btn:hover {
            background: var(--accent);
            color: #fff;
            border-color: var(--accent);
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(108, 99, 255, 0.25);
        }

        .filter-btn:active {
            transform: scale(0.94);
        }

        /* ============================================
                   TODO LIST
                   ============================================ */
        .todo-list-container {
            max-height: 420px;
            overflow-y: auto;
            margin-bottom: clamp(16px, 3vw, 20px);
            padding-right: 4px;
        }

        .todo-list-container::-webkit-scrollbar {
            width: 5px;
        }

        .todo-list-container::-webkit-scrollbar-track {
            background: var(--bg-primary);
            border-radius: 10px;
        }

        .todo-list-container::-webkit-scrollbar-thumb {
            background: var(--accent);
            border-radius: 10px;
        }

        .todo-list {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .todo-item {
            display: grid;
            grid-template-columns: auto 1fr auto;
            align-items: center;
            gap: clamp(10px, 2vw, 14px);
            padding: clamp(12px, 2vw, 16px);
            background: var(--bg-primary);
            border-radius: var(--border-radius-md);
            transition: all var(--transition);
            animation: slideIn 0.3s ease;
            min-height: 56px;
            position: relative;
        }

        .todo-item:hover {
            transform: translateX(4px);
            box-shadow: var(--shadow-sm);
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-12px) scale(0.96);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .todo-item.completed {
            opacity: 0.65;
        }

        .todo-item.completed .todo-text {
            text-decoration: line-through;
            color: var(--text-secondary);
        }

        /* Checkbox */
        .todo-item .checkbox {
            width: clamp(22px, 4vw, 26px);
            height: clamp(22px, 4vw, 26px);
            min-width: clamp(22px, 4vw, 26px);
            border: 2.5px solid var(--accent);
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all var(--transition);
            background: transparent;
            -webkit-tap-highlight-color: transparent;
            flex-shrink: 0;
        }

        .todo-item .checkbox:hover {
            background: var(--accent-light);
            transform: scale(1.05);
        }

        .todo-item .checkbox:active {
            transform: scale(0.9);
        }

        .todo-item .checkbox.checked {
            background: var(--accent);
            border-color: var(--accent);
        }

        .todo-item .checkbox.checked i {
            display: block;
            color: #fff;
            font-size: clamp(10px, 1.5vw, 12px);
        }

        .todo-item .checkbox i {
            display: none;
        }

        /* Todo Text */
        .todo-item .todo-text {
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            color: var(--text-primary);
            word-break: break-word;
            line-height: 1.4;
            padding: 2px 0;
        }

        /* Edit Input */
        .todo-item.editing .todo-text {
            display: none;
        }

        .todo-item.editing .edit-input {
            display: block;
        }

        .edit-input {
            display: none;
            width: 100%;
            padding: 6px 12px;
            border: 2px solid var(--accent);
            border-radius: var(--border-radius-sm);
            background: var(--bg-secondary);
            color: var(--text-primary);
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            font-family: inherit;
            outline: none;
            min-height: 38px;
        }

        .edit-input:focus {
            box-shadow: 0 0 0 4px rgba(108, 99, 255, 0.15);
        }

        /* Actions */
        .todo-item .todo-actions {
            display: flex;
            gap: 4px;
            flex-shrink: 0;
        }

        .todo-item .todo-actions button {
            background: none;
            border: none;
            cursor: pointer;
            padding: 6px 8px;
            border-radius: var(--border-radius-sm);
            transition: all var(--transition);
            font-size: clamp(0.85rem, 1.2vw, 1rem);
            color: var(--text-secondary);
            -webkit-tap-highlight-color: transparent;
            min-width: 36px;
            min-height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .todo-item .todo-actions .edit-btn:hover {
            background: var(--warning);
            color: #fff;
            transform: scale(1.05);
        }

        .todo-item .todo-actions .delete-btn:hover {
            background: var(--danger);
            color: #fff;
            transform: scale(1.05);
        }

        .todo-item .todo-actions button:active {
            transform: scale(0.9);
        }

        /* ============================================
                   CLEAR BUTTON
                   ============================================ */
        .clear-btn {
            width: 100%;
            padding: clamp(12px, 2vw, 14px);
            background: var(--danger);
            color: #fff;
            border: none;
            border-radius: var(--border-radius-md);
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            font-weight: 600;
            cursor: pointer;
            transition: all var(--transition);
            opacity: 0.7;
            font-family: inherit;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            -webkit-tap-highlight-color: transparent;
            min-height: 48px;
        }

        .clear-btn:hover:not(:disabled) {
            opacity: 1;
            transform: translateY(-1px);
            box-shadow: 0 4px 16px rgba(239, 68, 68, 0.3);
        }

        .clear-btn:active:not(:disabled) {
            transform: scale(0.97);
        }

        .clear-btn:disabled {
            opacity: 0.3;
            cursor: not-allowed;
            transform: none;
        }

        /* ============================================
                   EMPTY STATE
                   ============================================ */
        .empty-state {
            text-align: center;
            padding: clamp(30px, 8vw, 50px) clamp(16px, 4vw, 30px);
            color: var(--text-secondary);
        }

        .empty-state i {
            font-size: clamp(2.5rem, 6vw, 4rem);
            margin-bottom: 16px;
            opacity: 0.3;
            display: block;
        }

        .empty-state p {
            font-size: clamp(0.95rem, 1.8vw, 1.1rem);
            font-weight: 500;
        }

        .empty-state .sub-text {
            font-size: clamp(0.8rem, 1.2vw, 0.9rem);
            opacity: 0.7;
            margin-top: 6px;
        }

        /* ============================================
                   TOAST NOTIFICATION
                   ============================================ */
        .toast {
            position: fixed;
            bottom: 24px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: var(--bg-secondary);
            color: var(--text-primary);
            padding: 12px 24px;
            border-radius: var(--border-radius-md);
            box-shadow: var(--shadow-lg);
            font-weight: 500;
            font-size: 0.9rem;
            z-index: 999;
            opacity: 0;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid var(--bg-input);
            max-width: 90%;
            text-align: center;
            pointer-events: none;
        }

        .toast.show {
            opacity: 1;
            transform: translateX(-50%) translateY(0);
        }

        /* ============================================
                   RESPONSIVE BREAKPOINTS
                   ============================================ */

        /* Small phones (320px - 480px) */
        @media (max-width: 480px) {
            body {
                padding: 10px;
                align-items: flex-start;
                padding-top: 16px;
            }

            .app-container {
                padding: 16px;
                border-radius: var(--border-radius-lg);
            }

            .header h1 {
                font-size: 1.3rem;
            }

            .input-section {
                flex-direction: column;
                gap: 8px;
            }

            .input-section button {
                width: 100%;
                justify-content: center;
                min-height: 44px;
            }

            .input-section input {
                min-height: 44px;
            }

            .stats {
                grid-template-columns: 1fr 1fr 1fr;
                gap: 4px;
                padding: 10px;
            }

            .stat-item .count {
                font-size: 1.1rem;
            }

            .todo-item {
                grid-template-columns: auto 1fr auto;
                gap: 8px;
                padding: 10px 12px;
                min-height: 48px;
            }

            .todo-item .todo-actions button {
                min-width: 32px;
                min-height: 32px;
                padding: 4px 6px;
            }

            .filters {
                gap: 4px;
            }

            .filter-btn {
                padding: 6px 12px;
                font-size: 0.7rem;
                min-height: 32px;
                flex: 1;
            }

            .clear-btn {
                min-height: 44px;
                font-size: 0.85rem;
            }

            .todo-list-container {
                max-height: 300px;
            }
        }

        /* Medium phones (481px - 768px) */
        @media (min-width: 481px) and (max-width: 768px) {
            .app-container {
                padding: 24px;
            }

            .input-section button {
                min-height: 48px;
            }

            .filter-btn {
                min-height: 36px;
            }
        }

        /* Tablets (769px - 1024px) */
        @media (min-width: 769px) and (max-width: 1024px) {
            .app-container {
                padding: 32px;
            }
        }

        /* Large screens (1025px+) */
        @media (min-width: 1025px) {
            .app-container {
                padding: 40px;
            }

            .todo-item:hover {
                transform: translateX(6px);
            }
        }

        /* Landscape phones */
        @media (max-height: 600px) and (orientation: landscape) {
            body {
                align-items: flex-start;
                padding-top: 12px;
            }

            .app-container {
                padding: 16px;
            }

            .stats {
                padding: 8px 12px;
                margin-bottom: 12px;
            }

            .todo-list-container {
                max-height: 200px;
            }

            .header {
                margin-bottom: 12px;
            }

            section {
                padding: 12px 0;
            }
        }

        /* Dark mode support for system preference */
        @media (prefers-color-scheme: dark) {
            :root:not([data-theme="light"]) {
                --bg-primary: #0f0f1a;
                --bg-secondary: #1a1a2e;
                --bg-input: #252540;
                --text-primary: #f0f0f5;
                --text-secondary: #a0a0b8;
                --accent-light: #2a2555;
                --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.3);
                --shadow-md: 0 4px 20px rgba(0, 0, 0, 0.4);
                --shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.5);
            }
        }

        /* Reduced motion preferences */
        @media (prefers-reduced-motion: reduce) {
            *,
            *::before,
            *::after {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
            }

            .todo-item {
                animation: none !important;
            }
        }

        /* Touch-friendly targets */
        @media (hover: none) and (pointer: coarse) {
            .todo-item:hover {
                transform: none !important;
            }

            .todo-item .checkbox:hover {
                transform: none !important;
            }

            .todo-item .todo-actions button:hover {
                transform: none !important;
            }

            .filter-btn:hover {
                transform: none !important;
            }

            .input-section button:hover {
                transform: none !important;
            }

            .clear-btn:hover:not(:disabled) {
                transform: none !important;
            }
        }

        /* High contrast mode */
        @media (prefers-contrast: high) {
            .todo-item {
                border: 1px solid var(--text-secondary);
            }

            .todo-item .checkbox {
                border-width: 3px;
            }
        }
    </style>
</head>
<body>

    <!-- ==========================================
    APP CONTAINER
    ========================================== -->
    <div class="app-container" role="main" aria-label="Todo List Application">

        <!-- HEADER -->
        <header class="header">
            <div class="header-left">
                <span class="header-emoji" aria-hidden="true">📋</span>
                <h1><span>Todo</span> List</h1>
            </div>
            <div class="header-controls">
                <button id="theme-toggle" aria-label="Toggle dark mode" title="Toggle theme">
                    <i class="fas fa-moon"></i>
                </button>
            </div>
        </header>

        <!-- STATS -->
        <section class="stats" aria-label="Task statistics">
            <div class="stat-item">
                Total
                <span class="count" id="total-count">0</span>
            </div>
            <div class="stat-item">
                Completed
                <span class="count completed-count" id="completed-count">0</span>
            </div>
            <div class="stat-item">
                Pending
                <span class="count pending-count" id="pending-count">0</span>
            </div>
        </section>

        <!-- INPUT SECTION -->
        <section class="input-section" aria-label="Add new task">
            <div class="input-wrapper">
                <i class="fas fa-plus" aria-hidden="true"></i>
                <input
                type="text"
                id="todo-input"
                placeholder="Add a new task..."
                maxlength="100"
                autocomplete="off"
                aria-label="New task input"
                />
            </div>
            <button id="add-btn" aria-label="Add task">
                <i class="fas fa-plus" aria-hidden="true"></i>
                <span class="btn-text">Add</span>
            </button>
        </section>

        <!-- FILTERS -->
        <nav class="filters" aria-label="Filter tasks">
            <button class="filter-btn active" data-filter="all" aria-current="page">All</button>
            <button class="filter-btn" data-filter="active">Active</button>
            <button class="filter-btn" data-filter="completed">Completed</button>
        </nav>

        <!-- TODO LIST -->
        <section class="todo-list-container" aria-label="Task list">
            <ul class="todo-list" id="todo-list" role="list">
                <!-- Tasks rendered here -->
            </ul>
        </section>

        <!-- CLEAR BUTTON -->
        <button class="clear-btn" id="clear-btn" disabled aria-label="Clear all completed tasks">
            <i class="fas fa-trash" aria-hidden="true"></i>
            Clear All Completed
        </button>

    </div>

    <!-- TOAST NOTIFICATION -->
    <div class="toast" id="toast" role="alert" aria-live="polite"></div>

    <!-- ==========================================
    JAVASCRIPT
    ========================================== -->
    <script>
        document.addEventListener('DOMContentLoaded', function() {

            // ==========================================
            // STATE
            // ==========================================
            let todos = [];
            let currentFilter = 'all';
            let editingId = null;

            // ==========================================
            // DOM REFERENCES
            // ==========================================
            const todoInput = document.getElementById('todo-input');
            const addBtn = document.getElementById('add-btn');
            const todoList = document.getElementById('todo-list');
            const totalCount = document.getElementById('total-count');
            const completedCount = document.getElementById('completed-count');
            const pendingCount = document.getElementById('pending-count');
            const clearBtn = document.getElementById('clear-btn');
            const filterBtns = document.querySelectorAll('.filter-btn');
            const themeToggle = document.getElementById('theme-toggle');
            const themeIcon = themeToggle.querySelector('i');
            const toast = document.getElementById('toast');
            let toastTimeout = null;

            // ==========================================
            // TOAST NOTIFICATION
            // ==========================================
            function showToast(message, duration = 2500) {
                toast.textContent = message;
                toast.classList.add('show');

                if (toastTimeout) {
                    clearTimeout(toastTimeout);
                }

                toastTimeout = setTimeout(() => {
                    toast.classList.remove('show');
                }, duration);
            }

            // ==========================================
            // LOCAL STORAGE
            // ==========================================
            function loadTodos() {
                const stored = localStorage.getItem('todos');
                if (stored) {
                    try {
                        todos = JSON.parse(stored);
                    } catch (e) {
                        todos = getDefaultTodos();
                    }
                } else {
                    todos = getDefaultTodos();
                }
                render();
            }

            function getDefaultTodos() {
                return [
                    { id: Date.now() + 1, text: 'Learn JavaScript', completed: false },
                    { id: Date.now() + 2, text: 'Build a Todo App', completed: true },
                    { id: Date.now() + 3, text: 'Deploy to GitHub', completed: false },
                    { id: Date.now() + 4, text: 'Share with friends', completed: false },
                ];
            }

            function saveTodos() {
                try {
                    localStorage.setItem('todos', JSON.stringify(todos));
                } catch (e) {
                    console.warn('Failed to save todos:', e);
                }
            }

            // ==========================================
            // RENDER
            // ==========================================
            function render() {
                // Filter todos
                let filteredTodos = todos;
                if (currentFilter === 'active') {
                    filteredTodos = todos.filter(t => !t.completed);
                } else if (currentFilter === 'completed') {
                    filteredTodos = todos.filter(t => t.completed);
                }

                // Sort: incomplete first, then by id
                filteredTodos.sort((a, b) => {
                    if (a.completed !== b.completed) return a.completed ? 1 : -1;
                    return a.id - b.id;
                });

                // Update stats
                const total = todos.length;
                const completed = todos.filter(t => t.completed).length;
                const pending = total - completed;

                totalCount.textContent = total;
                completedCount.textContent = completed;
                pendingCount.textContent = pending;

                // Enable/disable clear button
                clearBtn.disabled = completed === 0;

                // Render list
                if (filteredTodos.length === 0) {
                    let message = 'No tasks yet. Add one above!';
                    let subText = '';
                    if (currentFilter === 'active') {
                        message = '🎉 All tasks completed!';
                        subText = 'Great job!';
                    } else if (currentFilter === 'completed') {
                        message = 'No completed tasks yet.';
                        subText = 'Complete a task to see it here.';
                    }

                    todoList.innerHTML = `
                                <div class="empty-state">
                                    <i class="fas fa-clipboard-list" aria-hidden="true"></i>
                                    <p>${message}</p>
                                    ${subText ? `<div class="sub-text">${subText}</div>` : ''}
                                </div>
                            `;
                    return;
                }

                todoList.innerHTML = filteredTodos.map(todo => `
                            <li class="todo-item ${todo.completed ? 'completed' : ''} ${editingId === todo.id ? 'editing' : ''}" 
                                data-id="${todo.id}" role="listitem">
                                <div class="checkbox ${todo.completed ? 'checked' : ''}" 
                                     data-action="toggle" 
                                     role="checkbox" 
                                     aria-checked="${todo.completed}"
                                     tabindex="0"
                                     aria-label="${todo.completed ? 'Mark as incomplete' : 'Mark as complete'}">
                                    <i class="fas fa-check" aria-hidden="true"></i>
                                </div>
                                <span class="todo-text">${escapeHtml(todo.text)}</span>
                                <input type="text" class="edit-input" value="${escapeHtml(todo.text)}" maxlength="100" aria-label="Edit task" />
                                <div class="todo-actions">
                                    <button class="edit-btn" data-action="edit" aria-label="Edit task">
                                        <i class="fas fa-pen" aria-hidden="true"></i>
                                    </button>
                                    <button class="delete-btn" data-action="delete" aria-label="Delete task">
                                        <i class="fas fa-trash" aria-hidden="true"></i>
                                    </button>
                                </div>
                            </li>
                        `).join('');

                // Save to localStorage
                saveTodos();
            }

            // ==========================================
            // ESCAPE HTML
            // ==========================================
            function escapeHtml(text) {
                const div = document.createElement('div');
                div.textContent = text;
                return div.innerHTML;
            }

            // ==========================================
            // ADD TODO
            // ==========================================
            function addTodo() {
                const text = todoInput.value.trim();
                if (!text) {
                    todoInput.focus();
                    todoInput.style.borderColor = '#ef4444';
                    showToast('Please enter a task!', 1500);
                    setTimeout(() => {
                        todoInput.style.borderColor = '';
                    }, 1500);
                    return;
                }

                const newTodo = {
                    id: Date.now(),
                    text: text,
                    completed: false,
                };

                todos.unshift(newTodo);
                todoInput.value = '';
                todoInput.focus();
                render();
                showToast('✅ Task added!', 1500);

                // If filter is 'completed', switch to 'all' to show new task
                if (currentFilter === 'completed') {
                    currentFilter = 'all';
                    filterBtns.forEach(b => b.classList.remove('active'));
                    document.querySelector('[data-filter="all"]').classList.add('active');
                }
            }

            // ==========================================
            // TOGGLE TODO
            // ==========================================
            function toggleTodo(id) {
                const todo = todos.find(t => t.id === id);
                if (todo) {
                    todo.completed = !todo.completed;
                    render();
                    const status = todo.completed ? 'completed' : 'active';
                    showToast(`✅ Task marked as ${status}!`, 1200);
                }
            }

            // ==========================================
            // DELETE TODO
            // ==========================================
            function deleteTodo(id) {
                const todo = todos.find(t => t.id === id);
                if (!todo) return;

                if (confirm(`Delete "${todo.text}"?`)) {
                    todos = todos.filter(t => t.id !== id);
                    if (editingId === id) editingId = null;
                    render();
                    showToast('🗑️ Task deleted!', 1500);
                }
            }

            // ==========================================
            // START EDIT
            // ==========================================
            function startEdit(id) {
                if (editingId === id) {
                    saveEdit(id);
                    return;
                }

                const todo = todos.find(t => t.id === id);
                if (todo) {
                    editingId = id;
                    render();
                    // Focus the edit input after render
                    requestAnimationFrame(() => {
                        const editInput = document.querySelector(`.todo-item[data-id="${id}"] .edit-input`);
                        if (editInput) {
                            editInput.focus();
                            editInput.select();
                        }
                    });
                }
            }

            // ==========================================
            // SAVE EDIT
            // ==========================================
            function saveEdit(id) {
                const todo = todos.find(t => t.id === id);
                if (!todo) return;

                const editInput = document.querySelector(`.todo-item[data-id="${id}"] .edit-input`);
                if (!editInput) return;

                const newText = editInput.value.trim();
                if (!newText) {
                    editingId = null;
                    render();
                    showToast('Edit cancelled', 1200);
                    return;
                }

                const oldText = todo.text;
                todo.text = newText;
                editingId = null;
                render();
                if (oldText !== newText) {
                    showToast('✏️ Task updated!', 1500);
                }
            }

            // ==========================================
            // CANCEL EDIT
            // ==========================================
            function cancelEdit() {
                if (editingId !== null) {
                    editingId = null;
                    render();
                }
            }

            // ==========================================
            // CLEAR COMPLETED
            // ==========================================
            function clearCompleted() {
                const completed = todos.filter(t => t.completed);
                if (completed.length === 0) return;

                if (confirm(`Delete ${completed.length} completed task(s)?`)) {
                    todos = todos.filter(t => !t.completed);
                    render();
                    showToast(`🗑️ Cleared ${completed.length} completed tasks!`, 2000);
                }
            }

            // ==========================================
            // EVENT DELEGATION (Click)
            // ==========================================
            todoList.addEventListener('click', function(e) {
                const target = e.target.closest('[data-action]');
                if (!target) return;

                const li = target.closest('.todo-item');
                if (!li) return;

                const id = parseInt(li.dataset.id);
                if (isNaN(id)) return;

                const action = target.dataset.action;

                if (action === 'toggle') {
                    toggleTodo(id);
                } else if (action === 'delete') {
                    deleteTodo(id);
                } else if (action === 'edit') {
                    startEdit(id);
                }
            });

            // ==========================================
            // KEYBOARD EVENTS
            // ==========================================
            // Edit input: Enter to save, Escape to cancel
            todoList.addEventListener('keydown', function(e) {
                const target = e.target;

                if (target.classList.contains('edit-input')) {
                    if (e.key === 'Enter') {
                        e.preventDefault();
                        const li = target.closest('.todo-item');
                        if (li) {
                            const id = parseInt(li.dataset.id);
                            if (!isNaN(id)) {
                                saveEdit(id);
                            }
                        }
                    } else if (e.key === 'Escape') {
                        e.preventDefault();
                        cancelEdit();
                    }
                }
            });

            // Checkbox: Enter/Space to toggle
            todoList.addEventListener('keydown', function(e) {
                const target = e.target.closest('.checkbox');
                if (target && (e.key === 'Enter' || e.key === ' ')) {
                    e.preventDefault();
                    const li = target.closest('.todo-item');
                    if (li) {
                        const id = parseInt(li.dataset.id);
                        if (!isNaN(id)) {
                            toggleTodo(id);
                        }
                    }
                }
            });

            // ==========================================
            // ADD BUTTON & INPUT
            // ==========================================
            addBtn.addEventListener('click', addTodo);

            todoInput.addEventListener('keydown', function(e) {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    addTodo();
                }
            });

            // ==========================================
            // FILTER BUTTONS
            // ==========================================
            filterBtns.forEach(btn => {
                btn.addEventListener('click', function() {
                    filterBtns.forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    currentFilter = this.dataset.filter;
                    // Cancel any ongoing edit
                    if (editingId !== null) {
                        editingId = null;
                    }
                    render();
                });
            });

            // ==========================================
            // CLEAR BUTTON
            // ==========================================
            clearBtn.addEventListener('click', clearCompleted);

            // ==========================================
            // THEME TOGGLE
            // ==========================================
            let currentTheme = localStorage.getItem('todo-theme') || 'light';
            document.documentElement.setAttribute('data-theme', currentTheme);
            updateIcon(currentTheme);

            themeToggle.addEventListener('click', function() {
                let theme = document.documentElement.getAttribute('data-theme');
                let newTheme = theme === 'light' ? 'dark' : 'light';
                document.documentElement.setAttribute('data-theme', newTheme);
                localStorage.setItem('todo-theme', newTheme);
                updateIcon(newTheme);
                showToast(newTheme === 'dark' ? '🌙 Dark mode enabled' : '☀️ Light mode enabled', 1500);
            });

            function updateIcon(theme) {
                if (theme === 'dark') {
                    themeIcon.className = 'fas fa-sun';
                } else {
                    themeIcon.className = 'fas fa-moon';
                }
            }

            // ==========================================
            // KEYBOARD SHORTCUTS (Global)
            // ==========================================
            document.addEventListener('keydown', function(e) {
                // Ctrl+Shift+A to focus input
                if (e.ctrlKey && e.shiftKey && (e.key === 'a' || e.key === 'A')) {
                    e.preventDefault();
                    todoInput.focus();
                    todoInput.select();
                }
                // Escape to cancel editing
                if (e.key === 'Escape' && editingId !== null) {
                    cancelEdit();
                }
            });

            // ==========================================
            // TOUCH FRIENDLY: Prevent double-tap zoom on buttons
            // ==========================================
            document.querySelectorAll('button, .checkbox').forEach(el => {
                el.addEventListener('touchend', function(e) {
                    // Prevent double-tap zoom on iOS
                    // (only if not editing)
                    if (!this.closest('.edit-input')) {
                        // Slight delay to let the click event fire
                    }
                }, { passive: true });
            });

            // ==========================================
            // INIT
            // ==========================================
            loadTodos();

            // Focus input on load (desktop only)
            if (window.innerWidth > 768) {
                setTimeout(() => {
                    todoInput.focus();
                }, 300);
            }

            console.log('✅ Todo App initialized!');
            console.log('💡 Shortcuts: Ctrl+Shift+A to focus input, Escape to cancel edit');

        });
    </script>

</body>
</html>
