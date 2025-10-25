# Gestion des notes des étudiants

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestion des Notes Étudiants</title>
    <style>
        :root {
            --color-white: rgba(255, 255, 255, 1);
            --color-black: rgba(0, 0, 0, 1);
            --color-cream-50: rgba(252, 252, 249, 1);
            --color-cream-100: rgba(255, 255, 253, 1);
            --color-gray-200: rgba(245, 245, 245, 1);
            --color-gray-300: rgba(167, 169, 169, 1);
            --color-gray-400: rgba(119, 124, 124, 1);
            --color-slate-500: rgba(98, 108, 113, 1);
            --color-brown-600: rgba(94, 82, 64, 1);
            --color-charcoal-700: rgba(31, 33, 33, 1);
            --color-charcoal-800: rgba(38, 40, 40, 1);
            --color-slate-900: rgba(19, 52, 59, 1);
            --color-teal-300: rgba(50, 184, 198, 1);
            --color-teal-400: rgba(45, 166, 178, 1);
            --color-teal-500: rgba(33, 128, 141, 1);
            --color-teal-600: rgba(29, 116, 128, 1);
            --color-teal-700: rgba(26, 104, 115, 1);
            --color-red-400: rgba(255, 84, 89, 1);
            --color-red-500: rgba(192, 21, 47, 1);
            --color-orange-400: rgba(230, 129, 97, 1);
            --color-orange-500: rgba(168, 75, 47, 1);
            --color-brown-600-rgb: 94, 82, 64;
            --color-teal-500-rgb: 33, 128, 141;
            --color-slate-900-rgb: 19, 52, 59;
            --color-slate-500-rgb: 98, 108, 113;
            --color-background: var(--color-cream-50);
            --color-surface: var(--color-cream-100);
            --color-text: var(--color-slate-900);
            --color-text-secondary: var(--color-slate-500);
            --color-primary: var(--color-teal-500);
            --color-primary-hover: var(--color-teal-600);
            --color-primary-active: var(--color-teal-700);
            --color-secondary: rgba(var(--color-brown-600-rgb), 0.12);
            --color-secondary-hover: rgba(var(--color-brown-600-rgb), 0.2);
            --color-border: rgba(var(--color-brown-600-rgb), 0.2);
            --color-btn-primary-text: var(--color-cream-50);
            --color-card-border: rgba(var(--color-brown-600-rgb), 0.12);
            --color-error: var(--color-red-500);
            --color-success: var(--color-teal-500);
            --color-warning: var(--color-orange-500);
            --font-family-base: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            --font-size-sm: 12px;
            --font-size-base: 14px;
            --font-size-lg: 16px;
            --font-size-xl: 18px;
            --font-size-2xl: 20px;
            --font-size-3xl: 24px;
            --font-weight-normal: 400;
            --font-weight-medium: 500;
            --font-weight-semibold: 550;
            --font-weight-bold: 600;
            --space-4: 4px;
            --space-8: 8px;
            --space-12: 12px;
            --space-16: 16px;
            --space-20: 20px;
            --space-24: 24px;
            --space-32: 32px;
            --radius-base: 8px;
            --radius-md: 10px;
            --radius-lg: 12px;
            --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.04), 0 1px 2px rgba(0, 0, 0, 0.02);
            --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.04), 0 2px 4px -1px rgba(0, 0, 0, 0.02);
        }

        @media (prefers-color-scheme: dark) {
            :root {
                --color-gray-400-rgb: 119, 124, 124;
                --color-teal-300-rgb: 50, 184, 198;
                --color-gray-300-rgb: 167, 169, 169;
                --color-gray-200-rgb: 245, 245, 245;
                --color-background: var(--color-charcoal-700);
                --color-surface: var(--color-charcoal-800);
                --color-text: var(--color-gray-200);
                --color-text-secondary: rgba(var(--color-gray-300-rgb), 0.7);
                --color-primary: var(--color-teal-300);
                --color-primary-hover: var(--color-teal-400);
                --color-secondary: rgba(var(--color-gray-400-rgb), 0.15);
                --color-secondary-hover: rgba(var(--color-gray-400-rgb), 0.25);
                --color-border: rgba(var(--color-gray-400-rgb), 0.3);
                --color-error: var(--color-red-400);
                --color-success: var(--color-teal-300);
                --color-warning: var(--color-orange-400);
                --color-btn-primary-text: var(--color-slate-900);
                --color-card-border: rgba(var(--color-gray-400-rgb), 0.2);
            }
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-family-base);
            font-size: var(--font-size-base);
            color: var(--color-text);
            background-color: var(--color-background);
            line-height: 1.5;
        }

        .app-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: var(--space-24);
        }

        .header {
            background: var(--color-surface);
            padding: var(--space-24);
            border-radius: var(--radius-lg);
            margin-bottom: var(--space-24);
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--color-card-border);
        }

        .header h1 {
            font-size: var(--font-size-3xl);
            font-weight: var(--font-weight-bold);
            margin-bottom: var(--space-8);
        }

        .header p {
            color: var(--color-text-secondary);
            margin-bottom: var(--space-16);
        }

        .btn-group {
            display: flex;
            gap: var(--space-12);
            flex-wrap: wrap;
        }

        .btn {
            padding: var(--space-12) var(--space-20);
            border: none;
            border-radius: var(--radius-base);
            font-size: var(--font-size-base);
            font-weight: var(--font-weight-medium);
            cursor: pointer;
            transition: all 0.2s;
            display: inline-flex;
            align-items: center;
            gap: var(--space-8);
        }

        .btn-primary {
            background: var(--color-primary);
            color: var(--color-btn-primary-text);
        }

        .btn-primary:hover {
            background: var(--color-primary-hover);
        }

        .btn-secondary {
            background: var(--color-secondary);
            color: var(--color-text);
        }

        .btn-secondary:hover {
            background: var(--color-secondary-hover);
        }

        .tabs {
            display: flex;
            gap: var(--space-8);
            margin-bottom: var(--space-24);
            border-bottom: 2px solid var(--color-border);
        }

        .tab {
            padding: var(--space-12) var(--space-24);
            background: none;
            border: none;
            font-size: var(--font-size-base);
            font-weight: var(--font-weight-medium);
            color: var(--color-text-secondary);
            cursor: pointer;
            border-bottom: 3px solid transparent;
            margin-bottom: -2px;
            transition: all 0.2s;
        }

        .tab.active {
            color: var(--color-primary);
            border-bottom-color: var(--color-primary);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .card {
            background: var(--color-surface);
            border-radius: var(--radius-lg);
            padding: var(--space-24);
            margin-bottom: var(--space-24);
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--color-card-border);
        }

        .card h2 {
            font-size: var(--font-size-xl);
            font-weight: var(--font-weight-semibold);
            margin-bottom: var(--space-16);
        }

        .form-group {
            margin-bottom: var(--space-16);
        }

        .form-label {
            display: block;
            font-weight: var(--font-weight-medium);
            margin-bottom: var(--space-8);
            font-size: var(--font-size-base);
        }

        .form-control {
            width: 100%;
            padding: var(--space-12);
            border: 1px solid var(--color-border);
            border-radius: var(--radius-base);
            font-size: var(--font-size-base);
            background: var(--color-surface);
            color: var(--color-text);
            transition: border-color 0.2s;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--color-primary);
        }

        .search-box {
            position: relative;
            margin-bottom: var(--space-20);
        }

        .search-box input {
            padding-left: var(--space-32);
        }

        .search-icon {
            position: absolute;
            left: var(--space-12);
            top: 50%;
            transform: translateY(-50%);
            color: var(--color-text-secondary);
        }

        .student-list {
            max-height: 500px;
            overflow-y: auto;
        }

        .student-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: var(--space-16);
            border: 1px solid var(--color-border);
            border-radius: var(--radius-base);
            margin-bottom: var(--space-8);
            cursor: pointer;
            transition: all 0.2s;
        }

        .student-item:hover {
            background: var(--color-secondary);
            border-color: var(--color-primary);
        }

        .student-info {
            flex: 1;
        }

        .student-name {
            font-weight: var(--font-weight-semibold);
            font-size: var(--font-size-base);
            margin-bottom: var(--space-4);
        }

        .student-meta {
            font-size: var(--font-size-sm);
            color: var(--color-text-secondary);
        }

        .student-grade {
            font-size: var(--font-size-xl);
            font-weight: var(--font-weight-bold);
            color: var(--color-primary);
        }

        .badge {
            display: inline-block;
            padding: var(--space-4) var(--space-8);
            border-radius: var(--radius-base);
            font-size: var(--font-size-sm);
            font-weight: var(--font-weight-medium);
            margin-left: var(--space-8);
        }

        .badge-group {
            background: rgba(var(--color-teal-500-rgb), 0.15);
            color: var(--color-primary);
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: var(--color-surface);
            border-radius: var(--radius-lg);
            padding: var(--space-32);
            max-width: 600px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: var(--space-24);
        }

        .modal-header h2 {
            margin: 0;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: var(--font-size-2xl);
            cursor: pointer;
            color: var(--color-text-secondary);
            padding: 0;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .close-btn:hover {
            color: var(--color-text);
        }

        .tp-list {
            display: flex;
            flex-direction: column;
            gap: var(--space-12);
        }

        .tp-item {
            display: flex;
            gap: var(--space-12);
            align-items: center;
            padding: var(--space-12);
            border: 1px solid var(--color-border);
            border-radius: var(--radius-base);
        }

        .tp-item input {
            flex: 1;
        }

        .btn-small {
            padding: var(--space-8) var(--space-12);
            font-size: var(--font-size-sm);
        }

        .grade-input-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
            gap: var(--space-12);
            margin-top: var(--space-16);
        }

        .grade-input-item {
            display: flex;
            flex-direction: column;
        }

        .grade-input-item label {
            font-size: var(--font-size-sm);
            margin-bottom: var(--space-4);
            font-weight: var(--font-weight-medium);
        }

        .grade-input-item input {
            padding: var(--space-8);
            text-align: center;
        }

        .filter-bar {
            display: flex;
            gap: var(--space-12);
            margin-bottom: var(--space-20);
            flex-wrap: wrap;
        }

        .filter-bar select {
            padding: var(--space-8) var(--space-12);
            border: 1px solid var(--color-border);
            border-radius: var(--radius-base);
            background: var(--color-surface);
            color: var(--color-text);
            font-size: var(--font-size-base);
        }

        .empty-state {
            text-align: center;
            padding: var(--space-32);
            color: var(--color-text-secondary);
        }

        .empty-state-icon {
            font-size: 48px;
            margin-bottom: var(--space-16);
        }

        .file-input-wrapper {
            position: relative;
            overflow: hidden;
            display: inline-block;
        }

        .file-input-wrapper input[type=file] {
            position: absolute;
            left: -9999px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: var(--space-16);
            margin-bottom: var(--space-24);
        }

        .stat-card {
            background: var(--color-secondary);
            padding: var(--space-20);
            border-radius: var(--radius-md);
            border: 1px solid var(--color-border);
        }

        .stat-value {
            font-size: var(--font-size-3xl);
            font-weight: var(--font-weight-bold);
            color: var(--color-primary);
        }

        .stat-label {
            font-size: var(--font-size-sm);
            color: var(--color-text-secondary);
            margin-top: var(--space-4);
        }

        .checkbox-wrapper {
            display: flex;
            align-items: center;
            gap: var(--space-8);
            margin-top: var(--space-12);
        }

        .checkbox-wrapper input[type="checkbox"] {
            width: 18px;
            height: 18px;
            cursor: pointer;
        }

        @media (max-width: 768px) {
            .app-container {
                padding: var(--space-16);
            }

            .btn-group {
                flex-direction: column;
            }

            .btn {
                width: 100%;
                justify-content: center;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }

            .grade-input-grid {
                grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <div class="header">
            <h1>📚 Gestion des Notes Étudiants</h1>
            <p>Importez, gérez et calculez les moyennes de vos étudiants</p>
            <div class="btn-group">
                <div class="file-input-wrapper">
                    <button class="btn btn-primary">📥 Importer CSV</button>
                    <input type="file" id="csvImport" accept=".csv">
                </div>
                <button class="btn btn-secondary" id="exportBtn">📤 Exporter CSV</button>
                <button class="btn btn-secondary" id="tpManageBtn">⚙️ Gérer les TP</button>
            </div>
        </div>

        <div class="tabs">
            <button class="tab active" data-tab="students">👥 Étudiants</button>
            <button class="tab" data-tab="grades">📝 Saisie des Notes</button>
            <button class="tab" data-tab="stats">📊 Statistiques</button>
        </div>

        <div id="studentsTab" class="tab-content active">
            <div class="card">
                <div class="filter-bar">
                    <div class="search-box" style="flex: 1;">
                        <span class="search-icon">🔍</span>
                        <input type="text" id="searchInput" class="form-control" placeholder="Rechercher un étudiant...">
                    </div>
                    <select id="groupFilter" class="form-control" style="width: auto; min-width: 150px;">
                        <option value="">Tous les groupes</option>
                    </select>
                </div>

                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value" id="totalStudents">0</div>
                        <div class="stat-label">Étudiants</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="totalGroups">0</div>
                        <div class="stat-label">Groupes</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="avgGlobal">-</div>
                        <div class="stat-label">Moyenne générale</div>
                    </div>
                </div>

                <div class="student-list" id="studentList">
                    <div class="empty-state">
                        <div class="empty-state-icon">📋</div>
                        <p>Aucun étudiant. Importez un fichier CSV pour commencer.</p>
                    </div>
                </div>
            </div>
        </div>

        <div id="gradesTab" class="tab-content">
            <div class="card">
                <h2>Saisie des notes</h2>
                <div class="form-group">
                    <label class="form-label">Sélectionner un étudiant</label>
                    <select id="studentSelect" class="form-control">
                        <option value="">-- Choisir un étudiant --</option>
                    </select>
                </div>

                <div class="checkbox-wrapper">
                    <input type="checkbox" id="binomeCheckbox">
                    <label for="binomeCheckbox">Saisir en binôme</label>
                </div>

                <div class="form-group" id="binomeSelectGroup" style="display: none; margin-top: var(--space-16);">
                    <label class="form-label">Sélectionner le binôme</label>
                    <select id="binomeSelect" class="form-control">
                        <option value="">-- Choisir un binôme --</option>
                    </select>
                </div>

                <div id="gradeInputsContainer"></div>

                <button class="btn btn-primary" id="saveGradesBtn" style="margin-top: var(--space-16);">💾 Enregistrer les notes</button>
            </div>
        </div>

        <div id="statsTab" class="tab-content">
            <div class="card">
                <h2>Statistiques par groupe</h2>
                <div id="statsContainer"></div>
            </div>
        </div>
    </div>

    <div id="tpModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Gestion des TP</h2>
                <button class="close-btn" id="closeTpModal">&times;</button>
            </div>
            <div class="form-group">
                <label class="form-label">Coefficient général</label>
                <input type="number" id="globalCoefficient" class="form-control" value="1" min="0.1" step="0.1">
            </div>
            <div id="tpListContainer" class="tp-list"></div>
            <button class="btn btn-secondary btn-small" id="addTpBtn" style="margin-top: var(--space-12);">+ Ajouter un TP</button>
            <button class="btn btn-primary" id="saveTpBtn" style="margin-top: var(--space-20); width: 100%;">Enregistrer</button>
        </div>
    </div>

    <script>
        const appState = {
            students: [],
            tps: [{name: 'TP1', maxGrade: 20}],
            coefficient: 1,
            currentStudent: null
        };

        function initApp() {
            loadFromMemory();
            setupEventListeners();
            renderStudentList();
            updateStats();
            renderTpList();
        }

        function setupEventListeners() {
            document.getElementById('csvImport').addEventListener('change', handleCsvImport);
            document.getElementById('exportBtn').addEventListener('click', exportToCsv);
            document.getElementById('tpManageBtn').addEventListener('click', () => {
                document.getElementById('tpModal').classList.add('active');
            });
            document.getElementById('closeTpModal').addEventListener('click', () => {
                document.getElementById('tpModal').classList.remove('active');
            });
            document.getElementById('addTpBtn').addEventListener('click', addTp);
            document.getElementById('saveTpBtn').addEventListener('click', saveTpConfig);
            document.getElementById('searchInput').addEventListener('input', handleSearch);
            document.getElementById('groupFilter').addEventListener('change', renderStudentList);
            document.getElementById('studentSelect').addEventListener('change', handleStudentSelect);
            document.getElementById('binomeCheckbox').addEventListener('change', handleBinomeCheckbox);
            document.getElementById('binomeSelect').addEventListener('change', () => {});
            document.getElementById('saveGradesBtn').addEventListener('click', saveGrades);

            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', () => {
                    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                    document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                    tab.classList.add('active');
                    const tabName = tab.getAttribute('data-tab');
                    document.getElementById(tabName + 'Tab').classList.add('active');
                    if (tabName === 'stats') {
                        renderStats();
                    }
                });
            });
        }

        function handleCsvImport(event) {
            const file = event.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = (e) => {
                const text = e.target.result;
                parseCsv(text);
            };
            reader.readAsText(file);
        }

        function parseCsv(text) {
            const lines = text.split('\n').filter(line => line.trim());
            if (lines.length < 2) {
                alert('Le fichier CSV est vide ou invalide.');
                return;
            }

            const headers = lines[0].split(',').map(h => h.trim());
            const students = [];

            for (let i = 1; i < lines.length; i++) {
                const values = lines[i].split(',').map(v => v.trim());
                if (values.length >= 3) {
                    students.push({
                        lastName: values[0] || '',
                        firstName: values[1] || '',
                        id: values[2] || '',
                        group: values[3] || 'Non assigné',
                        grades: {}
                    });
                }
            }

            appState.students = students;
            saveToMemory();
            renderStudentList();
            updateStats();
            populateGroupFilter();
            populateStudentSelect();
            alert(`${students.length} étudiants importés avec succès !`);
        }

        function exportToCsv() {
            if (appState.students.length === 0) {
                alert('Aucune donnée à exporter.');
                return;
            }

            let csv = 'Nom,Prénom,ID,Groupe';
            appState.tps.forEach(tp => {
                csv += `,${tp.name}`;
            });
            csv += ',Moyenne\n';

            appState.students.forEach(student => {
                csv += `${student.lastName},${student.firstName},${student.id},${student.group}`;
                appState.tps.forEach(tp => {
                    const grade = student.grades[tp.name] !== undefined ? student.grades[tp.name] : '';
                    csv += `,${grade}`;
                });
                const avg = calculateAverage(student);
                csv += `,${avg !== null ? avg.toFixed(2) : ''}\n`;
            });

            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = `notes_etudiants_${new Date().toISOString().split('T')[0]}.csv`;
            link.click();
        }

        function renderStudentList() {
            const searchTerm = document.getElementById('searchInput').value.toLowerCase();
            const groupFilter = document.getElementById('groupFilter').value;
            const container = document.getElementById('studentList');

            let filtered = appState.students.filter(student => {
                const matchesSearch = 
                    student.firstName.toLowerCase().includes(searchTerm) ||
                    student.lastName.toLowerCase().includes(searchTerm) ||
                    student.id.toLowerCase().includes(searchTerm);
                const matchesGroup = !groupFilter || student.group === groupFilter;
                return matchesSearch && matchesGroup;
            });

            if (filtered.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-state-icon">🔍</div>
                        <p>Aucun étudiant trouvé.</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = filtered.map(student => {
                const avg = calculateAverage(student);
                return `
                    <div class="student-item">
                        <div class="student-info">
                            <div class="student-name">
                                ${student.firstName} ${student.lastName}
                                <span class="badge badge-group">${student.group}</span>
                            </div>
                            <div class="student-meta">ID: ${student.id}</div>
                        </div>
                        <div class="student-grade">
                            ${avg !== null ? avg.toFixed(2) + '/20' : 'N/A'}
                        </div>
                    </div>
                `;
            }).join('');
        }

        function calculateAverage(student) {
            const grades = [];
            let totalCoef = 0;

            appState.tps.forEach(tp => {
                if (student.grades[tp.name] !== undefined && student.grades[tp.name] !== '') {
                    const normalizedGrade = (parseFloat(student.grades[tp.name]) / tp.maxGrade) * 20;
                    grades.push(normalizedGrade);
                    totalCoef += 1;
                }
            });

            if (grades.length === 0) return null;

            const sum = grades.reduce((a, b) => a + b, 0);
            return (sum / totalCoef) * appState.coefficient;
        }

        function updateStats() {
            document.getElementById('totalStudents').textContent = appState.students.length;
            
            const groups = [...new Set(appState.students.map(s => s.group))];
            document.getElementById('totalGroups').textContent = groups.length;

            const averages = appState.students.map(s => calculateAverage(s)).filter(a => a !== null);
            if (averages.length > 0) {
                const globalAvg = averages.reduce((a, b) => a + b, 0) / averages.length;
                document.getElementById('avgGlobal').textContent = globalAvg.toFixed(2) + '/20';
            } else {
                document.getElementById('avgGlobal').textContent = '-';
            }
        }

        function populateGroupFilter() {
            const groups = [...new Set(appState.students.map(s => s.group))];
            const select = document.getElementById('groupFilter');
            select.innerHTML = '<option value="">Tous les groupes</option>';
            groups.forEach(group => {
                select.innerHTML += `<option value="${group}">${group}</option>`;
            });
        }

        function populateStudentSelect() {
            const select = document.getElementById('studentSelect');
            select.innerHTML = '<option value="">-- Choisir un étudiant --</option>';
            appState.students.forEach((student, index) => {
                select.innerHTML += `<option value="${index}">${student.firstName} ${student.lastName} (${student.group})</option>`;
            });
        }

        function handleStudentSelect(event) {
            const index = event.target.value;
            if (index === '') {
                document.getElementById('gradeInputsContainer').innerHTML = '';
                appState.currentStudent = null;
                return;
            }

            appState.currentStudent = parseInt(index);
            const student = appState.students[index];
            
            updateBinomeList(student);
            renderGradeInputs(student);
        }

        function handleBinomeCheckbox(event) {
            const binomeGroup = document.getElementById('binomeSelectGroup');
            if (event.target.checked) {
                binomeGroup.style.display = 'block';
            } else {
                binomeGroup.style.display = 'none';
                document.getElementById('binomeSelect').value = '';
            }
        }

        function updateBinomeList(student) {
            const binomeSelect = document.getElementById('binomeSelect');
            binomeSelect.innerHTML = '<option value="">-- Choisir un binôme --</option>';
            
            appState.students.forEach((s, index) => {
                if (s.group === student.group && index !== appState.currentStudent) {
                    binomeSelect.innerHTML += `<option value="${index}">${s.firstName} ${s.lastName}</option>`;
                }
            });
        }

        function renderGradeInputs(student) {
            const container = document.getElementById('gradeInputsContainer');
            
            container.innerHTML = `
                <h3 style="margin-top: var(--space-24); margin-bottom: var(--space-16); font-size: var(--font-size-lg);">
                    Notes de ${student.firstName} ${student.lastName}
                </h3>
                <div class="grade-input-grid">
                    ${appState.tps.map(tp => `
                        <div class="grade-input-item">
                            <label>${tp.name} (/${tp.maxGrade})</label>
                            <input type="number" 
                                   class="form-control" 
                                   data-tp="${tp.name}" 
                                   value="${student.grades[tp.name] || ''}" 
                                   min="0" 
                                   max="${tp.maxGrade}" 
                                   step="0.5">
                        </div>
                    `).join('')}
                </div>
            `;
        }

        function saveGrades() {
            if (appState.currentStudent === null) {
                alert('Veuillez sélectionner un étudiant.');
                return;
            }

            const student = appState.students[appState.currentStudent];
            const inputs = document.querySelectorAll('#gradeInputsContainer input[type="number"]');
            
            inputs.forEach(input => {
                const tpName = input.getAttribute('data-tp');
                const value = input.value;
                student.grades[tpName] = value !== '' ? parseFloat(value) : undefined;
            });

            const binomeCheckbox = document.getElementById('binomeCheckbox');
            if (binomeCheckbox.checked) {
                const binomeIndex = document.getElementById('binomeSelect').value;
                if (binomeIndex !== '') {
                    const binome = appState.students[parseInt(binomeIndex)];
                    inputs.forEach(input => {
                        const tpName = input.getAttribute('data-tp');
                        const value = input.value;
                        binome.grades[tpName] = value !== '' ? parseFloat(value) : undefined;
                    });
                    alert(`Notes enregistrées pour ${student.firstName} et ${binome.firstName} (binôme) !`);
                } else {
                    alert('Veuillez sélectionner un binôme.');
                    return;
                }
            } else {
                alert(`Notes enregistrées pour ${student.firstName} ${student.lastName} !`);
            }

            saveToMemory();
            renderStudentList();
            updateStats();
        }

        function renderTpList() {
            const container = document.getElementById('tpListContainer');
            container.innerHTML = appState.tps.map((tp, index) => `
                <div class="tp-item">
                    <input type="text" class="form-control" placeholder="Nom du TP" value="${tp.name}" data-index="${index}" data-field="name">
                    <input type="number" class="form-control" placeholder="Note max" value="${tp.maxGrade}" min="1" step="0.5" data-index="${index}" data-field="maxGrade">
                    <button class="btn btn-secondary btn-small" onclick="removeTp(${index})">🗑️</button>
                </div>
            `).join('');

            document.getElementById('globalCoefficient').value = appState.coefficient;
        }

        function addTp() {
            appState.tps.push({name: `TP${appState.tps.length + 1}`, maxGrade: 20});
            renderTpList();
        }

        function removeTp(index) {
            if (appState.tps.length === 1) {
                alert('Il doit y avoir au moins un TP.');
                return;
            }
            appState.tps.splice(index, 1);
            renderTpList();
        }

        function saveTpConfig() {
            const inputs = document.querySelectorAll('#tpListContainer input');
            inputs.forEach(input => {
                const index = parseInt(input.getAttribute('data-index'));
                const field = input.getAttribute('data-field');
                if (field === 'name') {
                    appState.tps[index].name = input.value;
                } else if (field === 'maxGrade') {
                    appState.tps[index].maxGrade = parseFloat(input.value);
                }
            });

            appState.coefficient = parseFloat(document.getElementById('globalCoefficient').value);
            saveToMemory();
            populateStudentSelect();
            renderStudentList();
            updateStats();
            document.getElementById('tpModal').classList.remove('active');
            alert('Configuration des TP enregistrée !');
        }

        function handleSearch() {
            renderStudentList();
        }

        function renderStats() {
            const container = document.getElementById('statsContainer');
            const groups = [...new Set(appState.students.map(s => s.group))];

            if (groups.length === 0) {
                container.innerHTML = '<p style="color: var(--color-text-secondary);">Aucune statistique disponible.</p>';
                return;
            }

            container.innerHTML = groups.map(group => {
                const groupStudents = appState.students.filter(s => s.group === group);
                const averages = groupStudents.map(s => calculateAverage(s)).filter(a => a !== null);
                const groupAvg = averages.length > 0 
                    ? (averages.reduce((a, b) => a + b, 0) / averages.length).toFixed(2)
                    : 'N/A';

                return `
                    <div style="margin-bottom: var(--space-24); padding: var(--space-20); background: var(--color-secondary); border-radius: var(--radius-md); border: 1px solid var(--color-border);">
                        <h3 style="font-size: var(--font-size-xl); margin-bottom: var(--space-12);">${group}</h3>
                        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: var(--space-16);">
                            <div>
                                <div style="font-size: var(--font-size-2xl); font-weight: var(--font-weight-bold); color: var(--color-primary);">
                                    ${groupStudents.length}
                                </div>
                                <div style="font-size: var(--font-size-sm); color: var(--color-text-secondary);">Étudiants</div>
                            </div>
                            <div>
                                <div style="font-size: var(--font-size-2xl); font-weight: var(--font-weight-bold); color: var(--color-primary);">
                                    ${groupAvg}${groupAvg !== 'N/A' ? '/20' : ''}
                                </div>
                                <div style="font-size: var(--font-size-sm); color: var(--color-text-secondary);">Moyenne du groupe</div>
                            </div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function saveToMemory() {
            const data = {
                students: appState.students,
                tps: appState.tps,
                coefficient: appState.coefficient
            };
            try {
                const dataStr = JSON.stringify(data);
                document.cookie = `studentData=${encodeURIComponent(dataStr)}; max-age=31536000; path=/`;
            } catch (e) {
                console.log('Sauvegarde des données en mémoire');
            }
        }

        function loadFromMemory() {
            try {
                const cookies = document.cookie.split(';');
                for (let cookie of cookies) {
                    const [name, value] = cookie.trim().split('=');
                    if (name === 'studentData') {
                        const data = JSON.parse(decodeURIComponent(value));
                        appState.students = data.students || [];
                        appState.tps = data.tps || [{name: 'TP1', maxGrade: 20}];
                        appState.coefficient = data.coefficient || 1;
                        populateGroupFilter();
                        populateStudentSelect();
                        return;
                    }
                }
            } catch (e) {
                console.log('Aucune donnée sauvegardée trouvée');
            }
        }

        initApp();
    </script>
</body>
</html>
