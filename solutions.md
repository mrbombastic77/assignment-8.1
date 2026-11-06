HTML
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard-Style Grid Layout</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="dashboard-container">
        <!-- 1. Dashboard Header -->
        <header class="dashboard-header">
            <div class="logo">DevDashboard</div>
            <div class="user-profile">Atim Akhtar</div>
        </header>

        <!-- 2. Sidebar Navigation -->
        <aside class="dashboard-sidebar">
            <nav>
                <ul>
                    <li><a href="#" class="active">Overview</a></li>
                    <li><a href="#">Projects</a></li>
                    <li><a href="#">Analytics</a></li>
                    <li><a href="#">Settings</a></li>
                </ul>
            </nav>
        </aside>

        <!-- 3. Main Content Area with Statistic Cards -->
        <main class="dashboard-main">
            <div class="welcome-banner">
                <h2>Welcome back, Atim!</h2>
                <p>Here is an overview of your web development assignments and repository stats.</p>
            </div>

            <div class="stats-grid">
                <!-- Stat Card 1 -->
                <div class="stat-card">
                    <h3>Total Assignments</h3>
                    <p class="stat-number">24</p>
                    <span class="stat-badge positive">+3 this week</span>
                </div>

                <!-- Stat Card 2 -->
                <div class="stat-card">
                    <h3>Active Projects</h3>
                    <p class="stat-number">5</p>
                    <span class="stat-badge positive">On Track</span>
                </div>

                <!-- Stat Card 3 -->
                <div class="stat-card">
                    <h3>GitHub Commits</h3>
                    <p class="stat-number">142</p>
                    <span class="stat-badge positive">+12 today</span>
                </div>

                <!-- Stat Card 4 -->
                <div class="stat-card">
                    <h3>Code Reviews</h3>
                    <p class="stat-number">8</p>
                    <span class="stat-badge neutral">Pending</span>
                </div>
            </div>
        </main>
    </div>
</body>
</html>
CSS
/* style.css */
:root {
    --primary-color: #0284c7;
    --secondary-color: #0f172a;
    --sidebar-bg: #1e293b;
    --bg-color: #f8fafc;
    --surface-color: #ffffff;
    --text-color: #334155;
    --text-muted: #64748b;
    --border-color: #e2e8f0;
    --success-color: #10b981;
    
    --space-sm: 8px;
    --space-md: 16px;
    --space-lg: 24px;
    --space-xl: 32px;
    
    --radius-md: 8px;
    --radius-lg: 12px;
    --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.05);
    --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background-color: var(--bg-color);
    color: var(--text-color);
    line-height: 1.6;
}

/* 4 & 5. Outer Grid Layout Setup */
.dashboard-container {
    display: grid;
    grid-template-columns: 240px 1fr;
    grid-template-rows: 70px 1fr;
    min-height: 100vh;
    grid-template-areas:
        "header header"
        "sidebar main";
}

/* 1. Dashboard Header Styling */
.dashboard-header {
    grid-area: header;
    background-color: var(--surface-color);
    border-bottom: 1px solid var(--border-color);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 var(--space-xl);
    z-index: 10;
}

.logo {
    font-size: 1.25rem;
    font-weight: bold;
    color: var(--secondary-color);
}

.user-profile {
    font-weight: 600;
    color: var(--text-color);
}

/* 2. Sidebar Styling */
.dashboard-sidebar {
    grid-area: sidebar;
    background-color: var(--sidebar-bg);
    color: var(--surface-color);
    padding: var(--space-xl) var(--space-md);
}

.dashboard-sidebar nav ul {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
}

.dashboard-sidebar nav a {
    display: block;
    color: #94a3b8;
    text-decoration: none;
    font-weight: 500;
    padding: var(--space-sm) var(--space-md);
    border-radius: var(--radius-md);
    transition: background-color 0.2s ease, color 0.2s ease;
}

.dashboard-sidebar nav a:hover,
.dashboard-sidebar nav a.active {
    background-color: var(--primary-color);
    color: var(--surface-color);
}

/* 3 & 6. Main Content & Statistic Cards Grid */
.dashboard-main {
    grid-area: main;
    padding: var(--space-xl);
    display: flex;
    flex-direction: column;
    gap: var(--space-xl);
    overflow-y: auto;
}

.welcome-banner h2 {
    font-size: 1.75rem;
    color: var(--secondary-color);
    margin-bottom: 4px;
}

.welcome-banner p {
    color: var(--text-muted);
}

.stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: var(--space-lg);
}

.stat-card {
    background-color: var(--surface-color);
    border: 1px solid var(--border-color);
    border-radius: var(--radius-lg);
    padding: var(--space-lg);
    box-shadow: var(--shadow-sm);
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.stat-card:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-md);
}

.stat-card h3 {
    font-size: 0.95rem;
    color: var(--text-muted);
    font-weight: 500;
}

.stat-number {
    font-size: 2rem;
    font-weight: bold;
    color: var(--secondary-color);
}

.stat-badge {
    font-size: 0.75rem;
    font-weight: bold;
    padding: 2px 8px;
    border-radius: 4px;
    width: fit-content;
}

.stat-badge.positive {
    background-color: #dcfce7;
    color: var(--success-color);
}

.stat-badge.neutral {
    background-color: #f1f5f9;
    color: var(--text-muted);
}