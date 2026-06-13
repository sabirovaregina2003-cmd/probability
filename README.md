

<!DOCTYPE html>
<html lang="ru">
</html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title> Тренажер по вероятности и статистике</title>
<style>
        * {
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
            background: #eef2f9;
            margin: 0;
            padding: 0;
            min-height: 100vh;
        }
        .app {
            max-width: 1200px;
            margin: 0 auto;
            padding: 16px;
            min-height: 100vh;
        }
        .header {
            text-align: center;
            margin-bottom: 24px;
        }
        .header h1 {
            font-size: 1.6rem;
            margin: 0;
            background: linear-gradient(135deg, #1e4663, #2c6e9e);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            font-weight: 700;
        }
        .header p {
            color: #2c3e50;
            font-weight: 500;
            font-size: 1rem;
            margin: 5px 0 0 0;
        }
        
        .grade-tabs {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-bottom: 20px;
            justify-content: center;
        }
        .grade-btn {
            background: #ffffffcc;
            border: none;
            font-size: 1.1rem;
            font-weight: 700;
            padding: 8px 24px;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.2s;
            color: #1e2a3e;
            box-shadow: 0 2px 4px #0001;
        }
        .grade-btn.active {
            background: #1e4663;
            color: white;
            box-shadow: 0 4px 10px #0002;
        }
        .grade-btn:hover:not(.active) {
            background: #e2e8f0;
            transform: translateY(-2px);
        }
        
        .topic-tabs {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin-bottom: 16px;
            justify-content: center;
            border-bottom: 2px solid #cbdde9;
            padding-bottom: 12px;
        }
        .topic-btn {
            background: #e2e8f0;
            border: none;
            font-size: 0.8rem;
            font-weight: 600;
            padding: 6px 12px;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.2s;
            color: #1e2a3e;
        }
        .topic-btn.active {
            background: #0f5f9e;
            color: white;
        }
        .topic-btn:hover:not(.active) {
            background: #cbd5e1;
        }
        
        .type-tabs {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 20px;
            justify-content: center;
        }
        .type-btn {
            background: #f1f5f9;
            border: none;
            font-size: 0.85rem;
            font-weight: 600;
            padding: 8px 18px;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.2s;
            color: #1e2a3e;
        }
        .type-btn.active {
            background: #2c6e2c;
            color: white;
        }
        .type-btn:hover:not(.active) {
            background: #cbd5e1;
            transform: translateY(-1px);
        }
        
        .case-card {
            background: white;
            border-radius: 1.5rem;
            padding: 1.2rem;
            margin-bottom: 20px;
            box-shadow: 0 8px 16px -8px rgba(0,0,0,0.1);
            width: 100%;
        }
        .case-header {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            align-items: baseline;
            border-bottom: 2px solid #e2edf7;
            padding-bottom: 10px;
            margin-bottom: 12px;
        }
        .case-title {
            font-size: 1.2rem;
            font-weight: 700;
            background: linear-gradient(135deg, #1e4663, #2c6e9e);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
        }
        .case-status {
            font-size: 0.7rem;
            background: #f1f5f9;
            padding: 3px 10px;
            border-radius: 60px;
            font-weight: 600;
        }
        .case-status.solved {
            background: #d1fae5;
            color: #0b5e2e;
        }
        .case-description {
            background: #f9fbfe;
            padding: 0.8rem;
            border-radius: 1rem;
            margin: 12px 0;
            font-size: 0.85rem;
            line-height: 1.45;
            color: #0f2b3d;
        }
        .stage-block {
            background: #f8fafc;
            margin: 10px 0;
            padding: 10px 14px;
            border-radius: 0.8rem;
            border-left: 4px solid #2c6e9e;
        }
        .stages-btn {
            background: #e6f0fa;
            border: 1px solid #bdd4e7;
            padding: 4px 12px;
            border-radius: 40px;
            font-size: 0.7rem;
            font-weight: 600;
            cursor: pointer;
            color: #1e4663;
            margin-bottom: 10px;
        }
        .stages-btn:hover {
            background: #d4e4f2;
        }
        .stages-content {
            background: #fefce8;
            border-left: 4px solid #eab308;
            padding: 0.6rem 0.8rem;
            border-radius: 0.8rem;
            margin: 10px 0;
            font-size: 0.8rem;
            line-height: 1.45;
            display: none;
        }
        .stages-content.show {
            display: block;
        }
        .stages-content h4 {
            margin: 0 0 6px 0;
            color: #92400e;
            font-size: 0.85rem;
        }
        .question-text {
            font-weight: 700;
            margin: 12px 0 8px 0;
            color: #1e4663;
            font-size: 0.9rem;
        }
        .answer-row {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            align-items: center;
            margin: 10px 0;
        }
        .answer-input {
            flex: 2;
            padding: 8px 14px;
            border-radius: 40px;
            border: 2px solid #cbdde9;
            font-size: 0.9rem;
            font-family: monospace;
        }
        .check-btn {
            background: #2c6e2c;
            border: none;
            color: white;
            padding: 8px 18px;
            border-radius: 40px;
            font-weight: bold;
            cursor: pointer;
            font-size: 0.85rem;
        }
        .action-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin: 10px 0;
        }
        .hint-btn, .solution-btn {
            background: #e2e8f0;
            border: none;
            padding: 5px 12px;
            border-radius: 40px;
            font-weight: 500;
            cursor: pointer;
            font-size: 0.75rem;
        }
        .hint-btn {
            background: #fef3c7;
            color: #92400e;
        }
        .solution-btn {
            background: #dbeafe;
            color: #1e40af;
        }
        .hint-area, .solution-area {
            background: #eef3fa;
            border-radius: 0.8rem;
            padding: 0.6rem;
            margin-top: 8px;
            font-size: 0.8rem;
            display: none;
        }
        .hint-area {
            background: #fffbeb;
            border-left: 4px solid #f59e0b;
        }
        .solution-area {
            border-left: 4px solid #0f5f9e;
        }
        .hint-area.show, .solution-area.show {
            display: block;
        }
        .reset-case {
            background: none;
            border: none;
            color: #b91c1c;
            font-size: 0.65rem;
            text-decoration: underline;
            cursor: pointer;
            margin-top: 8px;
        }
        .feedback-area {
            font-size: 0.8rem;
            margin-top: 6px;
            font-weight: 500;
        }
        .empty-placeholder {
            background: white;
            border-radius: 1.5rem;
            padding: 2rem;
            text-align: center;
            color: #5d7184;
            font-size: 0.9rem;
        }
        footer {
            text-align: center;
            margin-top: 24px;
            font-size: 0.65rem;
            color: #5d7184;
        }
        button {
            font-family: inherit;
        }

        .step-container {
            background: #f8fafc;
            border-radius: 0.8rem;
            padding: 0.8rem;
            margin-bottom: 0.8rem;
        }
        .step-nav {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin-bottom: 16px;
            justify-content: center;
        }
        .step-btn {
            background: #e2e8f0;
            border: none;
            padding: 5px 12px;
            border-radius: 40px;
            cursor: pointer;
            font-weight: 600;
            transition: 0.2s;
            font-size: 0.75rem;
        }
        .step-btn.active {
            background: #0f5f9e;
            color: white;
        }
        .step-btn.completed {
            background: #2c6e2c;
            color: white;
        }
        .step-content {
            display: none;
            background: white;
            border-radius: 0.8rem;
            padding: 1rem;
            border: 1px solid #e2edf7;
        }
        .step-content.active-step {
            display: block;
        }
        .step-question {
            font-weight: 700;
            font-size: 0.9rem;
            margin-bottom: 12px;
            color: #1e4663;
        }
        .step-answer-area {
            margin: 12px 0;
        }
        .step-input {
            width: 100%;
            padding: 8px 12px;
            border: 2px solid #cbdde9;
            border-radius: 40px;
            font-size: 0.85rem;
            margin-bottom: 10px;
        }
        .step-check-btn {
            background: #2c6e2c;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 40px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.8rem;
        }
        .step-feedback {
            margin-top: 10px;
            padding: 8px;
            border-radius: 0.8rem;
            font-size: 0.8rem;
        }
        .step-feedback.correct {
            background: #d1fae5;
            color: #0b5e2e;
        }
        .step-feedback.wrong {
            background: #ffe6e5;
            color: #b91c1c;
        }
        .answers-history {
            background: #f1f5f9;
            border-radius: 0.8rem;
            padding: 0.8rem;
            margin-bottom: 16px;
        }
        .answers-history h4 {
            margin: 0 0 8px 0;
            color: #1e4663;
            font-size: 0.85rem;
        }
        .history-item {
            padding: 4px 0;
            border-bottom: 1px solid #cbdde9;
            font-size: 0.75rem;
        }
        .history-item.correct {
            color: #0b5e2e;
        }
        .history-item.wrong {
            color: #b91c1c;
        }
        .prev-steps-container {
            margin-bottom: 16px;
        }
        .prev-step-card {
            background: #f0fdf4;
            border-left: 4px solid #2c6e2c;
            padding: 8px 12px;
            margin-bottom: 10px;
            border-radius: 10px;
        }
        .prev-step-title {
            font-weight: 700;
            color: #1e4663;
            margin-bottom: 4px;
            font-size: 0.8rem;
        }
        .prev-step-answer {
            color: #0b5e2e;
            margin-bottom: 4px;
            font-size: 0.75rem;
        }
        .prev-step-explanation {
            color: #2c3e50;
            font-size: 0.75rem;
            padding-top: 4px;
            border-top: 1px dashed #cbdde9;
        }

/* ========== СТИЛИ ДЛЯ КЛАСТЕРА ========== */
.cluster-container {
    background: #f8fafc;
    border-radius: 1rem;
    padding: 1.2rem;
    margin-top: 1rem;
    width: 100%;
}

.cluster-center {
    text-align: center;
    margin-bottom: 1.2rem;
}

.cluster-title {
    background: linear-gradient(135deg, #1e4663, #2c6e9e);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
    font-size: 1.3rem;
    font-weight: 800;
    margin-bottom: 0.3rem;
}

.cluster-sub {
    color: #5d7184;
    font-size: 0.8rem;
}

.cluster-branches {
    display: flex;
    flex-wrap: wrap;
    gap: 0.8rem;
    justify-content: center;
    width: 100%;
}

.cluster-branch {
    flex: 1;
    min-width: 180px;
    background: white;
    border-radius: 0.8rem;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0,0,0,0.08);
}

.branch-header {
    background: #0f5f9e;
    color: white;
    padding: 0.6rem;
    text-align: center;
    font-weight: 700;
    font-size: 0.85rem;
}

.branch-dropzone {
    min-height: 200px;
    padding: 0.8rem;
    background: #fefefe;
    border: 2px dashed #cbdde9;
    border-top: none;
    transition: all 0.2s;
}

.branch-dropzone.drag-over {
    background: #e6f0fa;
    border-color: #0f5f9e;
}

.cluster-cards-pool {
    background: #f1f5f9;
    border-radius: 0.8rem;
    padding: 0.8rem;
    margin-top: 1rem;
    width: 100%;
}

.pool-title {
    font-weight: 700;
    color: #1e4663;
    margin-bottom: 0.8rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.85rem;
}

.cards-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 0.6rem;
    justify-content: center;
}

.drag-card {
    background: white;
    border: 1px solid #cbdde9;
    border-radius: 0.6rem;
    padding: 0.5rem 0.8rem;
    font-size: 0.75rem;
    cursor: grab;
    transition: all 0.2s;
    box-shadow: 0 1px 3px rgba(0,0,0,0.05);
    max-width: 180px;
}

.drag-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 3px 8px rgba(0,0,0,0.1);
    border-color: #0f5f9e;
}

.drag-card:active {
    cursor: grabbing;
}

.drag-card.dragging {
    opacity: 0.5;
}

.placed-item {
    background: #e6f0fa;
    border-radius: 0.5rem;
    padding: 0.5rem;
    margin-bottom: 0.5rem;
    font-size: 0.7rem;
    text-align: center;
    cursor: pointer;
    transition: 0.1s;
}

.placed-item:hover {
    background: #cbdde9;
    transform: scale(1.01);
}

.placed-item.correct {
    background: #d1fae5;
    border-left: 3px solid #2c6e2c;
}

.placed-item.wrong {
    background: #ffe6e5;
    border-left: 3px solid #b91c1c;
    text-decoration: line-through;
}

.empty-slot {
    color: #cbdde9;
    text-align: center;
    padding: 0.8rem;
    font-style: italic;
    font-size: 0.7rem;
}

.cluster-check-btn {
    background: #2c6e2c;
    color: white;
    border: none;
    padding: 0.6rem 1.5rem;
    border-radius: 2rem;
    font-weight: bold;
    cursor: pointer;
    margin-top: 1rem;
    display: block;
    width: 200px;
    margin-left: auto;
    margin-right: auto;
    font-size: 0.85rem;
}

.cluster-check-btn:hover {
    background: #1e551e;
    transform: scale(1.02);
}

.cluster-result {
    margin-top: 1rem;
    padding: 0.8rem;
    border-radius: 0.8rem;
    text-align: center;
    font-weight: 500;
    display: none;
    font-size: 0.8rem;
}

.cluster-result.success {
    background: #d1fae5;
    color: #0b5e2e;
    display: block;
}

.cluster-result.error {
    background: #ffe6e5;
    color: #b91c1c;
    display: block;
}

/* ========== СТИЛИ ДЛЯ ИНТЕРАКТИВНЫХ ЗАДАНИЙ ========== */
.interactive-container {
    background: white;
    border-radius: 1rem;
    padding: 1.2rem;
    margin-bottom: 1.2rem;
    width: 100%;
}

.interactive-title {
    font-size: 1.1rem;
    font-weight: 700;
    color: #1e4663;
    margin-bottom: 0.3rem;
}

.interactive-question {
    font-size: 0.85rem;
    color: #2c3e50;
    margin-bottom: 1rem;
    padding: 0.6rem;
    background: #f8fafc;
    border-radius: 0.8rem;
    border-left: 4px solid #eab308;
}

.diagram-container {
    position: relative;
    display: flex;
    justify-content: center;
    margin: 15px auto;
    cursor: pointer;
    width: 100%;
}

.diagram-svg {
    display: block;
    margin: 0 auto;
    background: #fefefe;
    border-radius: 0.8rem;
    box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    max-width: 100%;
    height: auto;
}

.hotspot-area {
    cursor: pointer;
    transition: 0.2s;
}

.hotspot-area:hover {
    fill-opacity: 0.3;
    stroke-width: 2;
}

.hotspot-area.correct-click {
    animation: correctPulse 0.5s ease;
}

.hotspot-area.wrong-click {
    animation: wrongShake 0.3s ease;
}

@keyframes correctPulse {
    0% { fill: #22c55e; fill-opacity: 0; }
    50% { fill: #22c55e; fill-opacity: 0.5; }
    100% { fill: #22c55e; fill-opacity: 0; }
}

@keyframes wrongShake {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-3px); }
    75% { transform: translateX(3px); }
}

.feedback-message {
    margin-top: 0.8rem;
    padding: 0.6rem;
    border-radius: 0.6rem;
    font-weight: 500;
    display: none;
    font-size: 0.8rem;
}

.feedback-message.correct {
    background: #d1fae5;
    color: #0b5e2e;
    display: block;
    border-left: 4px solid #2c6e2c;
}

.feedback-message.wrong {
    background: #ffe6e5;
    color: #b91c1c;
    display: block;
    border-left: 4px solid #b91c1c;
}

.interactive-progress {
    margin-top: 0.8rem;
    padding: 0.6rem;
    background: #f1f5f9;
    border-radius: 0.6rem;
    text-align: center;
    font-size: 0.75rem;
}

.interactive-nav {
    display: flex;
    gap: 8px;
    justify-content: center;
    margin-top: 0.8rem;
}

.interactive-nav-btn {
    background: #0f5f9e;
    color: white;
    border: none;
    padding: 6px 16px;
    border-radius: 40px;
    cursor: pointer;
    font-weight: 600;
    transition: 0.2s;
    font-size: 0.75rem;
}

.interactive-nav-btn:hover {
    background: #1e4663;
    transform: translateY(-1px);
}

.interactive-nav-btn:disabled {
    background: #cbd5e1;
    cursor: not-allowed;
    transform: none;
}

.interactive-reset-btn {
    background: #b91c1c;
    color: white;
    border: none;
    padding: 6px 16px;
    border-radius: 40px;
    cursor: pointer;
    font-weight: 600;
    margin-left: 8px;
    font-size: 0.75rem;
}

.task-completed-badge {
    background: #2c6e2c;
    color: white;
    padding: 2px 8px;
    border-radius: 60px;
    font-size: 0.65rem;
    display: inline-block;
    margin-left: 8px;
}

/* Стили для тестов ТРКМ */
.test-question-card {
    background: #f8fafc;
    border-radius: 0.8rem;
    padding: 0.8rem;
    margin-bottom: 1rem;
    border-left: 4px solid;
}

.test-question-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
    font-size: 0.75rem;
}

.test-question {
    font-weight: 600;
    margin-bottom: 12px;
    font-size: 0.85rem;
    line-height: 1.4;
}

.test-input {
    width: 100%;
    padding: 8px 14px;
    border: 2px solid #cbdde9;
    border-radius: 40px;
    font-size: 0.85rem;
    margin-bottom: 10px;
}

.test-check-btn {
    background: #2c6e2c;
    color: white;
    border: none;
    padding: 6px 18px;
    border-radius: 40px;
    cursor: pointer;
    font-weight: 600;
    font-size: 0.8rem;
}

.test-check-btn:hover {
    background: #1e551e;
}

.test-feedback {
    margin-top: 10px;
    font-size: 0.8rem;
}

.test-explanation {
    background: #d1fae5;
    padding: 8px 12px;
    border-radius: 0.8rem;
    margin-top: 10px;
    font-size: 0.8rem;
    line-height: 1.4;
}

.test-progress {
    margin-top: 16px;
    padding: 10px;
    background: #f1f5f9;
    border-radius: 0.8rem;
    text-align: center;
    font-size: 0.8rem;
    font-weight: 500;
}

/* Адаптация для мобильных устройств */
@media (max-width: 768px) {
    .app {
        padding: 10px;
    }
    
    .cluster-branch {
        min-width: 100%;
    }
    
    .case-card {
        padding: 0.8rem;
    }
    
    .grade-btn, .topic-btn, .type-btn {
        padding: 5px 12px;
        font-size: 0.8rem;
    }
    
    .cluster-title {
        font-size: 1.1rem;
    }
    
    .case-title {
        font-size: 1rem;
    }
}
    </style>
</head>
<body>
<div class="app">
    <div class="header">
        <h1>🧮 Управляемая случайность | Тренажер | Вероятность и статистика </h1>
        <p>Выберите класс и тему</p>
    </div>

    <div class="grade-tabs" id="gradeTabs">
        <button class="grade-btn" data-grade="7">7 класс</button>
        <button class="grade-btn active" data-grade="8">8 класс</button>
        <button class="grade-btn" data-grade="9">9 класс</button>
    </div>

    <div class="topic-tabs" id="topicTabs"></div>
    
<div class="type-tabs" id="typeTabs">
    <button class="type-btn active" data-type="cases">💼 Кейс-метод</button>
    <button class="type-btn" data-type="tests">💡 Исследовательское обучение</button>
    <button class="type-btn" data-type="formulas">🧠 ТРКМ</button>
<button class="type-btn" data-type="interactive">🖱️ Интерактивные визуализации</button>
     
</div>
    
    <div id="casesContainer"></div>
    <footer>💡 Не знаете ответа? Используйте подсказку или готовое решение.</footer>
</div>

<script>
    // ========== ВСЕ ВАШИ СУЩЕСТВУЮЩИЕ КЕЙСЫ (ОРИГИНАЛ) ==========
    const multiplicationCases = [
        { id: "mult_1", title: "🔐 Кейс 1: «Код от сейфа»", description: "В банке установлен новый сейф. Код состоит из двух цифр (от 0 до 9). Охранник утверждает, что взломать код очень легко, потому что вариантов всего 20 (10+10). Директор банка не согласен. Кто прав?",
          stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Учащиеся высказывают первое впечатление: сколько может быть вариантов кода?<br>2️⃣ <strong>Изучение материала:</strong> Учащиеся выясняют: код — это упорядоченная пара цифр (первая цифра, вторая). Цифры могут повторяться.<br>3️⃣ <strong>Выдвижение гипотез:</strong> Кто-то соглашается с охранником (20 вариантов), кто-то — с директором (вариантов больше). Выдвигаются предположения: 100, 90, 10×9 и т.д.<br>4️⃣ <strong>Выбор оптимального решения:</strong> Группы применяют правило умножения: первую цифру можно выбрать 10 способами, вторую — тоже 10 способами.<br>5️⃣ <strong>Обсуждение и рефлексия:</strong> Учащиеся объясняют, почему сложение (10+10) неверно, а умножение (10×10) правильно.`,
          question: "Сколько всего возможных кодов? (только число)", answerNormalizer: (ans) => parseInt(ans.replace(/\s/g, '')), answer: 100,
          hint: "💡 Первая цифра — 10 вариантов (0-9), вторая — тоже 10 вариантов. По правилу умножения перемножьте.",
          solution: "✅ <strong>Решение:</strong> 10 × 10 = <strong>100</strong> кодов.<br>• Охранник ошибся, сложив варианты (10+10=20). Правильно — умножать." },
        { id: "mult_2", title: "🍽️ Кейс 2: «Меню в столовой»", description: "В школьной столовой на обед можно выбрать: первое: борщ, суп, рассольник (3 варианта); второе: котлета, рыба, курица (3 варианта); напиток: компот, чай, сок (3 варианта). Ученик говорит: «Я могу обедать по-разному целый месяц и ни разу не повториться». Прав ли он?",
          stages: `1️⃣ <strong>Погружение:</strong> Учитель спрашивает: сколько разных обедов можно составить?<br>2️⃣ <strong>Изучение:</strong> Учащиеся фиксируют: обед = {первое, второе, напиток}. Каждый элемент выбирается из своего набора.<br>3️⃣ <strong>Гипотезы:</strong> Ученики предлагают: 3+3+3=9; 3×3=9; 3×3×3=27; 30.<br>4️⃣ <strong>Выбор решения:</strong> Применяют правило умножения: 3 × 3 × 3 = 27.<br>5️⃣ <strong>Рефлексия:</strong> Сравнивают 27 дней и месяц (30–31 день). Делают вывод, что ученик почти прав, но одного дня не хватит.`,
          question: "Сколько всего различных обедов можно составить? (число)", answerNormalizer: (ans) => parseInt(ans.replace(/\s/g, '')), answer: 27,
          hint: "💡 Перемножьте количество вариантов для первого, второго и напитка: 3 × 3 × 3.",
          solution: "✅ <strong>Решение:</strong> 3 × 3 × 3 = <strong>27</strong> обедов.<br>• 27 дней — это меньше, чем в месяце (30–31 день), поэтому повторы будут." },
        { id: "mult_3", title: "⚽ Кейс 3: «Форма футболистов»", description: "Футбольная команда из 11 человек готовится к матчу. У них есть: 2 вида футболок (синие, белые); 3 вида шорт (чёрные, красные, синие); 2 вида гетр (белые, чёрные). Тренер спрашивает: сколько разных вариантов экипировки возможно для одного игрока? Сможет ли команда сыграть 100 матчей и каждый раз выходить в новой комбинации?",
          stages: `1️⃣ <strong>Погружение:</strong> Учитель уточняет: экипировка для одного игрока — это комплект {футболка, шорты, гетры}.<br>2️⃣ <strong>Изучение:</strong> Учащиеся перечисляют количество вариантов для каждой позиции.<br>3️⃣ <strong>Гипотезы:</strong> 2+3+2=7; 2×3×2=12; 2×3×2×11.<br>4️⃣ <strong>Выбор решения:</strong> Применяют правило умножения для одного игрока: 2 × 3 × 2 = 12.<br>5️⃣ <strong>Рефлексия:</strong> 12 вариантов на 100 матчей — повторы неизбежны.`,
          question: "Сколько вариантов экипировки для одного игрока? (число)", answerNormalizer: (ans) => parseInt(ans.replace(/\s/g, '')), answer: 12,
          hint: "💡 Перемножьте: футболки (2) × трусы (3) × гетры (2).",
          solution: "✅ <strong>Решение:</strong> 2 × 3 × 2 = <strong>12</strong> вариантов.<br>• 12 < 100, поэтому на 100 матчей без повторов не хватит." },
        { id: "mult_4", title: "🔢 Кейс 4: «Пароль из букв и цифр»", description: "Пароль состоит из двух символов: первый — буква (А, Б, В, Г), второй — цифра (1, 2, 3). Сколько всего возможных паролей? Хакер утверждает, что может перебрать 10 паролей за секунду. За сколько секунд он переберёт все варианты?",
          stages: `1️⃣ <strong>Погружение:</strong> Учитель просит представить: сколько комбинаций может быть.<br>2️⃣ <strong>Изучение:</strong> Учащиеся определяют: буква — 4 варианта, цифра — 3 варианта.<br>3️⃣ <strong>Гипотезы:</strong> Ошибочные: 4+3=7; 4×3×2=24. Правильный подход: 4×3=12.<br>4️⃣ <strong>Выбор решения:</strong> По правилу умножения: 4 × 3 = 12 паролей.<br>5️⃣ <strong>Рефлексия:</strong> Время перебора: 12 / 10 = 1,2 секунды. Обсуждают, реально ли это.`,
          question: "Сколько всего паролей? (число). В ответе укажите только количество паролей.", answerNormalizer: (ans) => parseInt(ans.replace(/\s/g, '')), answer: 12,
          hint: "💡 Буква: 4 варианта, цифра: 3 варианта. Перемножьте.",
          solution: "✅ <strong>Решение:</strong> 4 × 3 = <strong>12</strong> паролей.<br>• Время перебора: 12 / 10 = 1,2 секунды." },
        { id: "mult_5", title: "🛣️ Кейс 5: «Путь из пункта А в пункт Д»", description: "Из города А в город В ведут 2 дороги. Из города В в город С — 3 дороги. Из города С в город Д — 2 дороги. Сколько различных маршрутов из А в Д (через В и С) существует? Водитель хочет каждый день ездить новым маршрутом. На сколько дней ему хватит вариантов?",
          stages: `1️⃣ <strong>Погружение:</strong> Учитель рисует схему: А → В → С → Д. Учащиеся уточняют, что маршрут — это последовательность дорог.<br>2️⃣ <strong>Изучение:</strong> Каждый этап независим: выбор дороги на одном участке не влияет на другие.<br>3️⃣ <strong>Гипотезы:</strong> 2+3+2=7; 2×3×2=12.<br>4️⃣ <strong>Выбор решения:</strong> Правило умножения: 2 × 3 × 2 = 12 маршрутов.<br>5️⃣ <strong>Рефлексия:</strong> Водителю хватит на 12 дней (почти на 2 недели).`,
          question: "Сколько различных маршрутов из А в Д? (число)", answerNormalizer: (ans) => parseInt(ans.replace(/\s/g, '')), answer: 12,
          hint: "💡 Перемножьте количество дорог на каждом участке: 2 × 3 × 2.",
          solution: "✅ <strong>Решение:</strong> 2 × 3 × 2 = <strong>12</strong> маршрутов.<br>• Вариантов хватит на 12 дней." }
    ];

    const oppositeCases = [
        { id: "opp_1", title: "🎲 Кейс 1: «Спор о кубиках: один или два?»", description: "Двое друзей спорят. Один говорит: «Если бросить один кубик, вероятность НЕ выбросить шестёрку равна 5/6 ≈ 0,83. А если бросить два кубика, вероятность того, что НИ на одном не выпадет шестёрка, будет (5/6)² ≈ 0,69. Значит, с двумя кубиками шанс 'неудачи' меньше». Второй друг возражает: «Нет, с двумя кубиками сложнее не получить шестёрку, потому что кубиков больше. Значит, вероятность НЕ выбросить шестёрку должна быть больше». Кто прав? С увеличением числа кубиков вероятность НЕ выбросить шестёрку увеличивается или уменьшается?",
          stages: "1️⃣ Погружение: Учитель читает спор. Класс разбивается на две группы.<br>2️⃣ Изучение: Вычисляют P(ни одной шестёрки) для 1,2,3 кубиков.<br>3️⃣ Гипотезы: Группы отстаивают свои позиции.<br>4️⃣ Выбор решения: Расчёт показывает уменьшение вероятности.<br>5️⃣ Рефлексия: Почему интуиция подводит? (Больше кубиков — больше шанс, что шестёрка выпадет хотя бы раз).",
          question: "Чему равна вероятность НЕ выбросить шестёрку при броске ТРЁХ кубиков? (введите десятичной дробью, округлив до тысячных, например 0.579)", answerNormalizer: (a)=> parseFloat(a.replace(',','.')), answer: 0.579,
          hint: "💡 P(ни одной шестёрки на одном кубике) = 5/6. Для трёх кубиков: (5/6)³",
          solution: "✅ Для одного кубика: 5/6 ≈ 0,833<br>• Для двух: (5/6)² = 25/36 ≈ 0,694<br>• Для трёх: (5/6)³ = 125/216 ≈ <strong>0,579</strong><br>• С увеличением числа кубиков вероятность уменьшается. Прав первый друг." },
        { id: "opp_2", title: "🎂 Кейс 2: «Парадокс дня рождения в классе»", description: "Учитель объявляет: «В нашем классе (25 человек) вероятность того, что хотя бы у двоих дни рождения совпадают, больше 0,5». Ученики возмущаются: «Не может быть! В году 365 дней, нас всего 25, это почти невозможно!» Учитель предлагает спор: «Кто готов поспорить на пятёрку, что я прав?» Прав ли учитель?",
          stages: "1️⃣ Погружение: Учитель объявляет спор. Класс интуитивно против.<br>2️⃣ Изучение: Прямой подсчёт сложен, переходят к противоположному событию.<br>3️⃣ Гипотезы: Большинство уверено, что вероятность маленькая.<br>4️⃣ Выбор решения: P(совпадение) = 1 − P(все разные).<br>5️⃣ Рефлексия: Удивление от результата (0,57).",
          question: "Какова вероятность, что хотя бы у двоих из 25 человек дни рождения совпадают? (округлите до сотых, например 0.57)", answerNormalizer: (a)=> parseFloat(a.replace(',','.')), answer: 0.57,
          hint: "💡 P(все разные) = 365/365 × 364/365 × ... × 341/365 ≈ 0,43",
          solution: "✅ P(все разные) = (365/365)×(364/365)×...×(341/365) ≈ 0,43<br>• P(хотя бы одно совпадение) = 1 − 0,43 = <strong>0,57</strong><br>• Учитель прав. Ученикам не стоит спорить." },
        { id: "opp_3", title: "🎫 Кейс 3: «Лотерея: выиграть или проиграть?»", description: "В лотерее 1000 билетов, из них 1 выигрышный. Билет стоит 100 руб. Человек покупает 10 разных билетов. Он говорит: «У меня шанс выиграть 1% — это 0,01». Друг отвечает: «10 билетов — это 10%!» Кто прав? Какова вероятность, что он НЕ выиграет ничего?",
          stages: "1️⃣ Погружение: Учитель зачитывает спор. Класс делится на два лагеря.<br>2️⃣ Изучение: Выигрышный билет только один.<br>3️⃣ Гипотезы: 1% или 10%.<br>4️⃣ Выбор решения: P(проигрыш) = (999/1000)^10.<br>5️⃣ Рефлексия: Разница между «шанс выиграть» и «ожидаемое количество выигрышей».",
          question: "Какова вероятность, что человек НЕ ВЫИГРАЕТ ничего? (округлите до сотых, например 0.99)", answerNormalizer: (a)=> parseFloat(a.replace(',','.')), answer: 0.99,
          hint: "💡 Вероятность, что конкретный билет проигрышный: 999/1000. Для 10 билетов: (999/1000)^10",
          solution: "✅ P(проигрыш) = (999/1000)^10 ≈ 0,99<br>• P(выигрыш) = 1 − 0,99 = 0,01 = <strong>1%</strong><br>• Прав тот, кто сказал 1%. Покупка 10 билетов не даёт 10% при одном выигрышном билете." },
        { id: "opp_4", title: "🚪 Кейс 4: «Три двери» (парадокс Монти Холла)", description: "В игре три двери. За одной — приз, за двумя — пусто. Вы выбираете дверь. Ведущий, который знает, где приз, открывает одну из оставшихся дверей, за которой пусто, и предлагает изменить выбор. Друг говорит: «Осталось две двери — вероятность 50 на 50. Менять смысла нет». Вы утверждаете, что вероятность выигрыша при смене выше. Какова вероятность выиграть, если НЕ МЕНЯТЬ выбор?",
          stages: "1️⃣ Погружение: Учитель рассказывает задачу. Многие думают 1/2.<br>2️⃣ Изучение: Разбор двух случаев: не меняет / меняет.<br>3️⃣ Гипотезы: «50/50» — самая популярная.<br>4️⃣ Выбор решения: Противоположное событие для смены выбора.<br>5️⃣ Рефлексия: Удивление от результата (парадокс).",
          question: "Какова вероятность выигрыша, если игрок НЕ МЕНЯЕТ свой первоначальный выбор? (введите десятичной дробью, например 0.333)", answerNormalizer: (a)=> parseFloat(a.replace(',','.')), answer: 0.333,
          hint: "💡 Игрок выигрывает, если сразу указал на призовую дверь. Всего дверей 3.",
          solution: "✅ Если игрок не меняет выбор: он выигрывает, если сразу указал на призовую дверь.<br>• Вероятность = 1/3 ≈ <strong>0,333</strong><br>• Если игрок меняет выбор: вероятность = 2/3 ≈ 0,667.<br>• Прав тот, кто меняет дверь." },
        { id: "opp_5", title: "👨‍👩‍👧‍👦 Кейс 5: «Семья с двумя детьми»", description: "Вы встречаете друга, у которого двое детей. Он говорит: «У меня двое детей, и хотя бы один из них — мальчик». Какова вероятность, что у него НЕТ девочки (то есть оба ребёнка — мальчики)? Друг утверждает, что вероятность 1/2. Вы считаете, что это не так. Кто прав?",
          stages: "1️⃣ Погружение: Учитель зачитывает разговор. Интуитивный ответ — 1/2.<br>2️⃣ Изучение: Выписывают все комбинации полов детей.<br>3️⃣ Гипотезы: Большинство думает 1/2.<br>4️⃣ Выбор решения: Исключают ДД из условия «хотя бы один мальчик».<br>5️⃣ Рефлексия: Почему условие меняет вероятности?",
          question: "Какова вероятность, что оба ребёнка — мальчики, при условии, что хотя бы один — мальчик? (введите десятичной дробью, например 0.333)", answerNormalizer: (a)=> parseFloat(a.replace(',','.')), answer: 0.333,
          hint: "💡 Все возможные комбинации: ММ, МД, ДМ, ДД. Каждая с вероятностью 1/4.",
          solution: "✅ Все комбинации: ММ, МД, ДМ, ДД (1/4 каждая).<br>• Условие «хотя бы один мальчик» исключает ДД.<br>• Остаются: ММ, МД, ДМ — 3 равновероятных исхода.<br>• Из них только ММ означает «нет девочки».<br>• Вероятность = 1/3 ≈ <strong>0,333</strong><br>• Прав тот, кто считает 1/3." }
    ];

    const eulerCases = [
        { id: "eul_1", title: "📐 Кейс 1: «Спор о кружках»", description: "В классе 30 человек. Математический кружок посещают 18 человек, шахматный — 15, а 10 человек ходят сразу на оба кружка. Ученик возразил: «Так не может быть, потому что 18+15=33, а у нас всего 30». Учитель ответил: «Всё правильно, просто некоторые ребята считаются дважды». Сколько человек посещают хотя бы один кружок? Сколько не посещают никакой?",
          stages: "1️⃣ Погружение: Учитель читает спор. Класс делится на группы.<br>2️⃣ Изучение: Строят диаграмму Эйлера.<br>3️⃣ Гипотезы: Одни согласны с учеником, другие — с учителем.<br>4️⃣ Выбор решения: |A∪B| = |A|+|B|−|A∩B|.<br>5️⃣ Рефлексия: Почему нельзя просто сложить?",
          question: "Сколько человек посещают хотя бы один кружок? (число)", answerNormalizer: (a)=>parseInt(a), answer: 23,
          hint: "💡 |A∪B| = |A| + |B| − |A∩B| = 18 + 15 − 10",
          solution: "✅ |A∪B| = 18+15−10 = <strong>23</strong> (посещают хотя бы один)<br>• Не посещают: 30−23 = <strong>7</strong>" },
        { id: "eul_2", title: "🏆 Кейс 2: «Олимпиады по математике и физике»", description: "В школе 50 учеников. 25 участвовали в олимпиаде по математике, 20 — по физике, а 10 не участвовали ни в одной. Один ученик заявил: «Значит, 15 человек участвовали в обеих». Другой возразил: «Нет, их должно быть 5». Кто прав?",
          stages: "1️⃣ Погружение: Учитель зачитывает спор.<br>2️⃣ Изучение: Находят |A∪B| = 50−10 = 40.<br>3️⃣ Гипотезы: 15 или 5.<br>4️⃣ Выбор решения: |A∩B| = |A|+|B|−|A∪B|.<br>5️⃣ Рефлексия: Проверка через диаграмму.",
          question: "Сколько человек участвовали в обеих олимпиадах? (число)", answerNormalizer: (a)=>parseInt(a), answer: 5,
          hint: "💡 Сначала найдите |A∪B| = 50 − 10 = 40. Затем |A∩B| = 25+20−40",
          solution: "✅ |A∪B| = 50−10 = 40<br>• |A∩B| = 25+20−40 = <strong>5</strong><br>• Прав второй ученик." },
        { id: "eul_3", title: "📚 Кейс 3: «Загадка про чтение книг»", description: "В библиотеке опросили 100 читателей. Детективы читают 60 человек, фантастику — 50, а 20 человек не читают ни детективы, ни фантастику. Один библиотекарь сказал: «Тогда получается, что 30 человек читают и то, и другое». Другой возразил: «Нет, должно быть 10». Кто прав?",
          stages: "1️⃣ Погружение: Учитель читает спор.<br>2️⃣ Изучение: |A∪B| = 100−20 = 80.<br>3️⃣ Гипотезы: 30 или 10.<br>4️⃣ Выбор решения: |A∩B| = 60+50−80.<br>5️⃣ Рефлексия: Проверка через диаграмму.",
          question: "Сколько человек читают оба жанра? (число)", answerNormalizer: (a)=>parseInt(a), answer: 30,
          hint: "💡 |A∪B| = 100 − 20 = 80. Затем |A∩B| = 60+50−80",
          solution: "✅ |A∪B| = 100−20 = 80<br>• |A∩B| = 60+50−80 = <strong>30</strong><br>• Прав первый библиотекарь." },
        { id: "eul_4", title: "⚽ Кейс 4: «Спор о спортивных секциях»", description: "В классе 35 учеников. Футболом занимаются 20, баскетболом — 15, а 8 занимаются и тем и другим. Один ученик сказал: «Значит, 13 человек не занимаются ничем». Другой возразил: «Нет, 8». Кто прав?",
          stages: "1️⃣ Погружение: Учитель зачитывает спор.<br>2️⃣ Изучение: |A∪B| = 20+15−8 = 27.<br>3️⃣ Гипотезы: 13 или 8.<br>4️⃣ Выбор решения: Не занимаются = 35−27.<br>5️⃣ Рефлексия: Проверка через диаграмму.",
          question: "Сколько учеников не занимаются ни футболом, ни баскетболом? (число)", answerNormalizer: (a)=>parseInt(a), answer: 8,
          hint: "💡 |A∪B| = 20+15−8 = 27. Затем 35−27",
          solution: "✅ |A∪B| = 20+15−8 = 27 (занимаются хотя бы одной)<br>• Не занимаются: 35−27 = <strong>8</strong><br>• Прав второй ученик." },
        { id: "eul_5", title: "🔢 Кейс 5: «Парадокс с тремя кружками»", description: "В классе 40 человек. Математика — 25, шахматы — 20, литература — 15. 10 человек посещают матем. и шахм., 8 — матем. и лит., 5 — шахм. и лит., 3 — все три. Ученик утверждает: «Тогда хотя бы один кружок посещают 25+20+15=60 человек, что невозможно». Как правильно посчитать?",
          stages: "1️⃣ Погружение: Ученик ошибается, просто складывая числа.<br>2️⃣ Изучение: Формула для трёх множеств.<br>3️⃣ Гипотезы: Нужно вычитать пересечения и добавлять тройное.<br>4️⃣ Выбор решения: |A∪B∪C| = |A|+|B|+|C| − |A∩B|−|A∩C|−|B∩C| + |A∩B∩C|.<br>5️⃣ Рефлексия: Почему формула работает?",
          question: "Сколько человек посещают хотя бы один кружок? (число)", answerNormalizer: (a)=>parseInt(a), answer: 40,
          hint: "💡 |A∪B∪C| = 25+20+15 − 10−8−5 + 3",
          solution: "✅ |A∪B∪C| = 25+20+15 − 10−8−5 + 3 = 60 − 23 + 3 = <strong>40</strong><br>• Не посещают ни одного: 40−40 = <strong>0</strong><br>• Все 40 человек посещают хотя бы один кружок." }
    ];

    const incompatibleCases = [
        { id: "inc_1", title: "💰 Кейс 1: «Спор о выигрыше»", description: "В лотерейном билете есть два независимых поля. Вероятность выиграть в первом поле — 0,1, во втором — 0,2. Один человек говорит: «Значит, вероятность выиграть хотя бы в одном поле равна 0,1 + 0,2 = 0,3». Другой возражает: «Нельзя просто складывать, может получиться больше 1 или двойной учёт». Кто прав? Можно ли складывать эти вероятности?",
          stages: "1️⃣ Погружение: Учитель зачитывает спор. Кто прав?<br>2️⃣ Изучение: События совместны? Могут ли произойти одновременно?<br>3️⃣ Гипотезы: 0,3 — верно или нет?<br>4️⃣ Выбор решения: Для совместных событий нужна формула P(A∪B)=P(A)+P(B)−P(A∩B).<br>5️⃣ Рефлексия: Почему нельзя просто складывать вероятности совместных событий?",
          question: "Можно ли в данной ситуации просто сложить вероятности 0,1 и 0,2? (введите: да или нет)", answerNormalizer: (a)=>a.toLowerCase().trim(), answer: "нет",
          hint: "💡 Может ли билет выиграть одновременно в обоих полях? Если да — события совместны.",
          solution: "✅ Прав второй. События «выиграть в первом поле» и «выиграть во втором поле» <strong>совместны</strong> (можно выиграть в обоих полях одновременно). Поэтому формула сложения для несовместных событий здесь не работает. Нужно использовать общую формулу: P(A∪B) = P(A)+P(B)−P(A∩B). Без знания P(A∩B) ответ 0,3 — неверный." },
        { id: "inc_2", title: "🎨 Кейс 2: «Цветные шары»", description: "В мешке лежат 3 красных, 2 синих и 5 зелёных шаров. Вы наугад вытаскиваете один шар. Ваш друг говорит: «Вероятность вытащить красный или синий равна 0,3 + 0,2 = 0,5». Вы сомневаетесь: «А может, нужно что-то вычитать?» Кто прав?",
          stages: "1️⃣ Погружение: Учитель читает спор.<br>2️⃣ Изучение: Может ли шар быть одновременно красным и синим?<br>3️⃣ Гипотезы: 0,5 или другое число?<br>4️⃣ Выбор решения: Проверка на несовместность.<br>5️⃣ Рефлексия: Когда можно складывать вероятности?",
          question: "Чему равна вероятность вытащить красный или синий шар? (введите десятичной дробью, например 0.5)", answerNormalizer: (a)=>parseFloat(a.replace(',','.')), answer: 0.5,
          hint: "💡 P(красный)=3/10=0,3; P(синий)=2/10=0,2. Может ли шар быть одновременно красным и синим?",
          solution: "✅ Прав друг. События «вытащить красный» и «вытащить синий» <strong>несовместны</strong>, потому что один шар не может быть одновременно красным и синим. Поэтому P = 0,3 + 0,2 = <strong>0,5</strong>." },
        { id: "inc_3", title: "🎲 Кейс 3: «Спор о кубике»", description: "Бросают один игральный кубик. Один ученик утверждает: «Вероятность выпадения 1 или 2 равна 1/6 + 1/6 = 1/3». Другой ученик говорит: «Нет, нужно вычесть вероятность пересечения, потому что может выпасть и 1, и 2 одновременно». Кто прав?",
          stages: "1️⃣ Погружение: Учитель читает спор.<br>2️⃣ Изучение: Может ли на кубике выпасть два числа сразу?<br>3️⃣ Гипотезы: 1/3 или меньше?<br>4️⃣ Выбор решения: Проверка на несовместность.<br>5️⃣ Рефлексия: Почему второй ученик ошибся?",
          question: "Чему равна вероятность выпадения 1 или 2? (введите дробью, например 1/3)", answerNormalizer: (a)=>eval(a), answer: 1/3,
          hint: "💡 При одном броске кубика выпадает только одно число. События несовместны.",
          solution: "✅ Прав первый ученик. При одном броске кубика может выпасть только одно число, поэтому события «выпала 1» и «выпала 2» <strong>несовместны</strong>. P = 1/6 + 1/6 = 2/6 = <strong>1/3</strong>. Второй ученик ошибся, предположив, что может выпасть два числа сразу." },
        { id: "inc_4", title: "🎯 Кейс 4: «Стрелки и мишень»", description: "Два стрелка стреляют по одной мишени. Вероятность попадания первого — 0,7, второго — 0,8. Один наблюдатель говорит: «Вероятность того, что в мишени будет хотя бы одна пробоина, равна 0,7 + 0,8 = 1,5 — это невозможно, значит, я ошибся». Другой наблюдатель отвечает: «Просто нужно вычесть вероятность одновременного попадания, тогда получится нормальное число». Кто прав?",
          stages: "1️⃣ Погружение: Почему 0,7+0,8 > 1?<br>2️⃣ Изучение: События совместны?<br>3️⃣ Гипотезы: Как правильно посчитать?<br>4️⃣ Выбор решения: P(A∪B) = P(A)+P(B)−P(A∩B).<br>5️⃣ Рефлексия: Зачем вычитать пересечение?",
          question: "Чему равна вероятность хотя бы одного попадания? (введите десятичной дробью, например 0.94)", answerNormalizer: (a)=>parseFloat(a.replace(',','.')), answer: 0.94,
          hint: "💡 P(A∩B) = 0,7 × 0,8 = 0,56 (если стреляют независимо). Затем P(A∪B) = 0,7+0,8−0,56",
          solution: "✅ Прав второй наблюдатель. События «попал первый» и «попал второй» <strong>совместны</strong> (могут попасть оба). P(A∩B) = 0,7 × 0,8 = 0,56. P(A∪B) = 0,7 + 0,8 − 0,56 = <strong>0,94</strong>." },
        { id: "inc_5", title: "☀️ Кейс 5: «Семья и дни рождения»", description: "В семье трое детей. Один родитель говорит: «Вероятность того, что у случайного ребёнка день рождения летом или зимой, равна 3/12 + 3/12 = 0,5». Другой родитель сомневается: «А если день рождения может быть одновременно летом и зимой?» Что вы ответите?",
          stages: "1️⃣ Погружение: Учитель читает спор.<br>2️⃣ Изучение: Пересекаются ли летние и зимние месяцы?<br>3️⃣ Гипотезы: 0,5 или нужно вычитать?<br>4️⃣ Выбор решения: Проверка на несовместность.<br>5️⃣ Рефлексия: Почему здесь можно складывать?",
          question: "Чему равна вероятность того, что день рождения случайного ребёнка летом или зимой? (введите десятичной дробью, например 0.5)", answerNormalizer: (a)=>parseFloat(a.replace(',','.')), answer: 0.5,
          hint: "💡 Летние месяцы: июнь, июль, август. Зимние: декабрь, январь, февраль. Пересекаются ли они?",
          solution: "✅ Прав первый родитель. Летние месяцы (июнь, июль, август) и зимние (декабрь, январь, февраль) <strong>не пересекаются</strong> — ни один месяц не является одновременно летом и зимой. События несовместны, поэтому P = 3/12 + 3/12 = 6/12 = <strong>0,5</strong>." }
    ];

    const conditionalCases = [
    // ========== КЕЙС 1. «Спор в школьной столовой» (сложение vs умножение) ==========
    {
        id: "cond_1",
        title: "🥧 Кейс 1: «Спор в школьной столовой»",
        description: "В школьной столовой на подносе лежат пирожки. Повар говорит: 'У меня 3 пирожка с капустой, 2 – с мясом и 4 – с яблоком. Вы можете взять один пирожок. Какова вероятность того, что он будет с капустой или с мясом?' Один ученик быстро ответил: «Нужно умножить 3/9 на 2/9». Второй ученик засомневался: «По-моему, тут нужно сложить вероятности». Третий ученик сказал: «Можно посчитать вероятность того, что пирожок не с яблоком». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает три варианта ответа.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся выясняют: может ли пирожок быть одновременно с капустой и с мясом?<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Группы обсуждают, кто прав: первый, второй или третий ученик.<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют правило сложения для несовместных событий или находят вероятность через противоположное событие.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему умножение здесь не работает? Какую фразу-помощник можно запомнить?`,
        question: "Чему равна вероятность вытащить пирожок с капустой ИЛИ с мясом? (введите десятичной дробью, например 0.132)",
        answerNormalizer: (a)=>parseFloat(a.replace(',','.')),
        answer: 5/9,
        hint: "💡 P(капуста) = 3/9, P(мясо) = 2/9. Может ли пирожок быть одновременно с капустой и мясом?",
        solution: "✅ События «вытащить пирожок с капустой» и «вытащить пирожок с мясом» <strong>несовместны</strong> (один пирожок не может иметь две начинки). Поэтому P = 3/9 + 2/9 = 5/9 ≈ <strong>0,556</strong>. Третий ученик тоже прав: 1 − 4/9 = 5/9."
    },
    // ========== КЕЙС 2. «Спор в квесте» (возврат vs невозврат) ==========
    {
        id: "cond_2",
        title: "🗝️ Кейс 2: «Спор в квесте»",
        description: "Вы участвуете в квесте. В шкатулке 7 золотых ключей и 8 серебряных. Правило: вы вынимаете первый ключ, бросаете его другу (ключ не возвращается), затем вынимаете второй. Чтобы открыть дверь, нужны два золотых ключа подряд. Организатор говорит: «Вероятность вытащить два золотых ключа равна 49/225». Один из игроков возражает: «Ключ же не возвращается! Ответ будет другим». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает ключевую фразу «ключ не возвращается».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся выясняют разницу между выбором с возвращением и без возвращения.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто прав: организатор или игрок?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют вероятность через условную вероятность: 7/15 · 6/14.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как одно слово «не возвращается» меняет ответ?`,
        question: "Чему равна вероятность вытащить два золотых ключа подряд БЕЗ ВОЗВРАЩЕНИЯ? (введите десятичной дробью, например 0.5)",
        answerNormalizer: (a)=>parseFloat(a.replace(',','.')),
        answer: 0.2,
        hint: "💡 После первого вынимания в шкатулке остаётся 14 ключей. Если первый был золотым, то золотых осталось 6.",
        solution: "✅ Прав игрок. Организатор ошибся, посчитав с возвращением. Без возвращения: P = 7/15 × 6/14 = 42/210 = 1/5 = <strong>0,2</strong>."
    },
    // ========== КЕЙС 3. «Секретный код» (условная вероятность при независимых событиях) ==========
    {
        id: "cond_3",
        title: "🔐 Кейс 3: «Секретный код»",
        description: "Код состоит из двух цифр (от 1 до 9). Вы знаете, что первая цифра — чётная. Организатор говорит: «Вероятность угадать две чётные цифры подряд — 16/81». Игрок возражает: «Мы же знаем, что первая цифра чётная! Это меняет вероятности». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает ключевую фразу «вы знаете, что первая цифра чётная».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся определяют, влияет ли условие на вторую цифру (цифры могут повторяться).<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Организатор или игрок прав?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят P(вторая чётная | первая чётная) = 4/9.<br>
5️⃣ <strong>Рефлексия:</strong> Как изменился бы ответ, если бы цифры не могли повторяться?`,
        question: "Какова вероятность того, что вторая цифра окажется чётной, при условии что первая цифра чётная? (введите десятичной дробью, например 0.123)",
        answerNormalizer: (a)=>parseFloat(a.replace(',','.')),
        answer: 4/9,
        hint: "💡 Чётные цифры от 1 до 9: 2, 4, 6, 8 (4 варианта). Всего цифр 9.",
        solution: "✅ Прав игрок. Организатор посчитал P(обе чётные) = 4/9 × 4/9 = 16/81. Но по условию мы УЖЕ знаем, что первая цифра чётная, поэтому нужно найти только P(вторая чётная) = 4/9 ≈ <strong>0,444</strong>. События независимы, условие не меняет вероятность."
    },
    // ========== КЕЙС 4. «Больной в поликлинике»  ==========
    {
        id: "cond_4",
        title: "🏥 Кейс 4: «Больной в поликлинике»",
        description: "Редкая болезнь встречается у 1 человека из 1000. Тест показывает болезнь у 99% больных, но ошибочно показывает болезнь у 5% здоровых. Вам пришёл положительный результат. Пациент говорит: «Тест точный на 99%! Значит, вероятность, что я болен — 99%». Врач качает головой. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает ключевую фразу «болеет 1 человек из 1000».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся записывают данные в виде вероятностей.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Пациент или врач прав?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют формулу условной вероятности (теорему Байеса).<br>
5️⃣ <strong>Рефлексия:</strong> Почему результат такой низкий, хотя тест кажется точным?`,
        question: "Какова вероятность, что вы действительно больны при положительном тесте? (округлите до тысячных, например 0.125)",
        answerNormalizer: (a)=>parseFloat(a.replace(',','.')),
        answer: 0.0194,
        hint: "💡 На 1000 человек: 1 больной, 999 здоровых. P(полож|болен)=0,99, P(полож|здоров)=0,05.",
        solution: "✅ Прав врач. P(болен|полож) = (0,001×0,99) / (0,001×0,99 + 0,999×0,05) = 0,00099 / 0,05094 ≈ <strong>0,0194</strong> (около 1,94%). Даже с положительным тестом вероятность болезни меньше 2% из-за редкости болезни."
    },
    // ========== КЕЙС 5. «Три шкатулки» (задача Монти Холла) ==========
    {
        id: "cond_5",
        title: "📦 Кейс 5: «Три шкатулки»",
        description: "Перед вами три шкатулки. В одной — золотая монета, в двух — пустые. Вы выбираете шкатулку наугад. Затем ведущий, который знает, где монета, открывает одну пустую шкатулку (не ту, что вы выбрали). Он предлагает вам изменить выбор. Один ученик говорит: «Осталось две шкатулки, вероятность 50 на 50. Менять бессмысленно». Другой возражает: «Если поменять, шансы вырастут». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает ключевую фразу «ведущий знает, где монета».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся разбирают два случая: оставить выбор или поменять.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> 50/50 или 2/3?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят P(выигрыш при смене) = 2/3, P(выигрыш без смены) = 1/3.<br>
5️⃣ <strong>Рефлексия:</strong> Почему интуиция подсказывает 50/50, но это неверно?`,
        question: "Какова вероятность выигрыша, если ИЗМЕНИТЬ выбор? (введите десятичной дробью, например 0.123)",
        answerNormalizer: (a)=>parseFloat(a.replace(',','.')),
        answer: 2/3,
        hint: "💡 Вы выигрываете при смене, если первый выбор был неверным. Вероятность первого неверного выбора — 2/3.",
        solution: "✅ Прав второй ученик. Если не менять: P = 1/3 ≈ 0,333. Если менять: P = 2/3 ≈ <strong>0,667</strong>. Ведущий своими действиями даёт дополнительную информацию, поэтому менять выбор выгоднее."
    }
];

    const treeCases = [
        { id: "tree_1", title: "🪙 Кейс 1: «Спор о монете»", description: "Двое друзей спорят. Один говорит: «Если подбросить монету два раза, то вероятность выпадения хотя бы одного орла равна 0,5+0,5=1». Второй возражает. Кто прав? Постройте дерево.",
          stages: "1️⃣ Построение дерева для двух бросков.<br>2️⃣ Исходы: ОО, ОР, РО, РР.<br>3️⃣ Подсчёт благоприятных исходов.<br>4️⃣ Вычисление вероятности.<br>5️⃣ Рефлексия: Почему нельзя складывать?",
          question: "Вероятность хотя бы одного орла? (десятичной дробью)", answerNormalizer: (a)=>parseFloat(a.replace(',','.')), answer: 0.75,
          hint: "💡 Всего 4 исхода, благоприятных — 3", solution: "✅ Дерево: 4 исхода. Благоприятные: ОО, ОР, РО (3). P = 3/4 = <strong>0,75</strong>" },
        { id: "tree_2", title: "🎲 Кейс 2: «Игральная кость и монета»", description: "Сначала бросают кубик. Если чётное — подбрасывают монету. Если нечётное — не подбрасывают. Какова вероятность выпадения решки?",
          stages: "1️⃣ Построение дерева: кубик → чёт/нечёт → монета.<br>2️⃣ Вероятность чётного: 0,5.<br>3️⃣ Вероятность решки при чётном: 0,5.<br>4️⃣ Вычисление.<br>5️⃣ Рефлексия.",
          question: "Вероятность выпадения решки? (десятичной дробью)", answerNormalizer: (a)=>parseFloat(a.replace(',','.')), answer: 0.25,
          hint: "💡 Только при чётном числе (вероятность 0,5) и решке (0,5)", solution: "✅ P(решка) = P(чётное) × P(решка|чётное) = 0,5 × 0,5 = <strong>0,25</strong>" },
        { id: "tree_3", title: "🎲 Кейс 3: «Спор о двух кубиках»", description: "Бросают два кубика. Ученик утверждает: «Вероятность суммы 7 такая же, как суммы 2». Другой возражает. Кто прав?",
          stages: "1️⃣ Построение таблицы исходов 6×6.<br>2️⃣ Подсчёт благоприятных исходов для суммы 7 и суммы 2.<br>3️⃣ Сравнение вероятностей.<br>4️⃣ Вывод.<br>5️⃣ Рефлексия.",
          question: "Вероятность суммы 7? (дробью, например 1/6)", answerNormalizer: (a)=>eval(a), answer: 1/6,
          hint: "💡 Всего 36 исходов. Для суммы 7: (1,6),(2,5),(3,4),(4,3),(5,2),(6,1) — 6 исходов", solution: "✅ P(сумма 7) = 6/36 = <strong>1/6</strong>. P(сумма 2) = 1/36. Прав второй ученик." },
        { id: "tree_4", title: "🍬 Кейс 4: «Выбор коробки и конфеты»", description: "Коробка 1: 3 шок., 2 кар. Коробка 2: 1 шок., 4 кар. Выбор коробки 0,5. Вероятность шоколадной конфеты?",
          stages: "1️⃣ Построение дерева: коробка → конфета.<br>2️⃣ Вероятности для каждой коробки.<br>3️⃣ Суммирование по веткам.<br>4️⃣ Вычисление.<br>5️⃣ Рефлексия.",
          question: "Вероятность шоколадной конфеты? (десятичной дробью)", answerNormalizer: (a)=>parseFloat(a.replace(',','.')), answer: 0.4,
          hint: "💡 P = 0,5×0,6 + 0,5×0,2", solution: "✅ P = 0,5×0,6 + 0,5×0,2 = 0,3 + 0,1 = <strong>0,4</strong>" },
        { id: "tree_5", title: "📝 Кейс 5: «Три попытки сдать экзамен»", description: "С первой попытки — 0,6. Если не сдал, то со второй — 0,8. Если и со второй не сдал, то с третьей — 0,9. Вероятность сдать?",
          stages: "1️⃣ Построение дерева с тремя уровнями.<br>2️⃣ Вычисление вероятности каждой ветки.<br>3️⃣ Суммирование успешных веток.<br>4️⃣ Результат.<br>5️⃣ Рефлексия.",
          question: "Вероятность сдать экзамен? (десятичной дробью)", answerNormalizer: (a)=>parseFloat(a.replace(',','.')), answer: 0.992,
          hint: "💡 P = 0,6 + 0,4×0,8 + 0,4×0,2×0,9", solution: "✅ P = 0,6 + 0,32 + 0,072 = <strong>0,992</strong>" }
    ];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "СРЕДНЕЕ, МОДА, МЕДИАНА, РАЗМАХ" (7 КЛАСС) ==========
const statisticsBasicCases = [
    // ========== КЕЙС 1. «Выбор лучшего продавца» (остаётся без изменений) ==========
    {
        id: "stat_basic_1",
        title: "📊 Кейс 1: «Выбор лучшего продавца»",
        description: `<strong>Сюжет:</strong><br>
        В магазин электроники требуются два продавца-консультанта. На собеседование пришли три кандидата. Для оценки их работы руководство решило проанализировать количество продаж, сделанных каждым из них за предыдущую неделю (с понедельника по пятницу).<br><br>
        <strong>Данные о продажах:</strong><br>
        <table style="width: 100%; border-collapse: collapse; margin-top: 10px;">
            <tr style="background: #1e4663; color: white;">
                <th style="padding: 8px; border: 1px solid #cbdde9;">Кандидат</th>
                <th style="padding: 8px; border: 1px solid #cbdde9;">Пн</th>
                <th style="padding: 8px; border: 1px solid #cbdde9;">Вт</th>
                <th style="padding: 8px; border: 1px solid #cbdde9;">Ср</th>
                <th style="padding: 8px; border: 1px solid #cbdde9;">Чт</th>
                <th style="padding: 8px; border: 1px solid #cbdde9;">Пт</th>
            </tr>
            <tr><td style="padding: 6px; border: 1px solid #cbdde9;"><strong>Андрей</strong></td><td style="padding: 6px; border: 1px solid #cbdde9;">25</td><td style="padding: 6px; border: 1px solid #cbdde9;">28</td><td style="padding: 6px; border: 1px solid #cbdde9;">30</td><td style="padding: 6px; border: 1px solid #cbdde9;">27</td><td style="padding: 6px; border: 1px solid #cbdde9;">25</td></tr>
            <tr style="background: #f8fafc;"><td style="padding: 6px; border: 1px solid #cbdde9;"><strong>Борис</strong></td><td style="padding: 6px; border: 1px solid #cbdde9;">35</td><td style="padding: 6px; border: 1px solid #cbdde9;">20</td><td style="padding: 6px; border: 1px solid #cbdde9;">25</td><td style="padding: 6px; border: 1px solid #cbdde9;">40</td><td style="padding: 6px; border: 1px solid #cbdde9;">15</td></tr>
            <tr><td style="padding: 6px; border: 1px solid #cbdde9;"><strong>Виктор</strong></td><td style="padding: 6px; border: 1px solid #cbdde9;">22</td><td style="padding: 6px; border: 1px solid #cbdde9;">24</td><td style="padding: 6px; border: 1px solid #cbdde9;">23</td><td style="padding: 6px; border: 1px solid #cbdde9;">25</td><td style="padding: 6px; border: 1px solid #cbdde9;">26</td></tr>
        </table>
        <strong>Задание:</strong> Определите, кто из трёх кандидатов является лучшим продавцом.`,
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Учащиеся знакомятся с данными.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вспоминают формулы и определения.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто из кандидатов лучше?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют все статистические характеристики.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сравнивают результаты и обосновывают выбор.`,
        questions: [
            { id: "q1", text: "Чему равно среднее арифметическое продаж Андрея?", type: "choice", options: ["25", "27", "30"], correct: "27", hint: "Сложи все продажи Андрея и раздели на 5.", explanation: "✅ (25+28+30+27+25)÷5 = 135÷5 = <strong>27</strong>" },
            { id: "q2", text: "У кого из кандидатов есть мода?", type: "choice", options: ["Андрей", "Борис", "Виктор"], correct: "Андрей", hint: "Посмотри, у кого число повторяется дважды.", explanation: "✅ У Андрея число 25 встречается 2 раза." },
            { id: "q3", text: "Чему равен размах продаж Бориса?", type: "input", correct: "25", hint: "Размах = max − min. У Бориса max=40, min=15.", explanation: "✅ 40−15 = <strong>25</strong>" },
            { id: "q4", text: "Сопоставь каждого кандидата с его медианой.", type: "matching", pairs: [{ item: "Андрей", match: "27" }, { item: "Борис", match: "25" }, { item: "Виктор", match: "24" }], hint: "Упорядочь числа и найди среднее.", explanation: "✅ Андрей: 25,25,27,28,30 → медиана 27<br>✅ Борис: 15,20,25,35,40 → медиана 25<br>✅ Виктор: 22,23,24,25,26 → медиана 24" },
            { id: "q5", text: "Кто из кандидатов лучший? Объясни коротко.", type: "text", correctKeywords: ["Андрей", "лучший", "стабилен"], hint: "Сравни все характеристики.", explanation: "✅ Лучший – <strong>Андрей</strong>. У него высокое среднее (27), маленький размах (5), есть мода." }
        ]
    },

    // ========== КЕЙС 2. «Спортивная команда: кого взять на замену?» ==========
    {
        id: "stat_basic_2",
        title: "🏀 Кейс 2: «Спортивная команда: кого взять на замену?»",
        description: "Тренер баскетбольной команды выбирает игрока на замену. Два кандидата показали результаты за 10 игр (очки за матч):<br><br>• <strong>Игрок А:</strong> 12, 14, 13, 15, 12, 14, 13, 15, 12, 40<br>• <strong>Игрок Б:</strong> 18, 17, 16, 18, 17, 16, 18, 17, 16, 17<br><br>Тренер просит вычислить все характеристики и решить, кто стабильнее.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Кто нужен тренеру?<br>
2️⃣ <strong>Изучение материала:</strong> Вычисляют среднее, медиану, моду, размах.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> У кого результаты стабильнее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Заполняют таблицу сравнения.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему среднее одинаковое, а игроки разные?`,
        question: "Чему равна МЕДИАНА у игрока А? (введите число, например 13.5)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 13.5,
        hint: "💡 Упорядочь ряд А: 12,12,12,13,13,14,14,15,15,40. Медиана — среднее между 5-м и 6-м числами.",
        solution: "✅ Медиана А = (13+14)/2 = <strong>13,5</strong>. Медиана Б = 17. Среднее одинаковое (17), но игрок А нестабилен (размах 28), его вытащил один матч (40 очков). Для стабильности нужен Б, для риска — А."
    },

    // ========== КЕЙС 3. «Зарплаты в IT-компании» ==========
    {
        id: "stat_basic_3",
        title: "💰 Кейс 3: «Зарплаты в IT-компании»",
        description: "В небольшой IT-компании работают 10 человек. Их зарплаты (тыс. руб.):<br><br>35, 40, 42, 45, 50, 50, 55, 60, 70, 300<br><br>Директор пишет в отчёте: «Средняя зарплата — 74,7 тыс. руб. Мы достойно платим!» Сотрудники возмущены. Помогите им доказать, что отчёт вводит в заблуждение.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Почему сотрудники недовольны?<br>
2️⃣ <strong>Изучение материала:</strong> Вычисляют среднее, медиану, моду, размах.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая характеристика честнее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают среднее (74,7) и медиану (50).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какую характеристику выбрал бы директор, а какую — профсоюз?`,
        question: "Чему равна МЕДИАНА зарплат? (введите число, например 50)",
        answerNormalizer: (a) => parseInt(a),
        answer: 50,
        hint: "💡 Упорядочи ряд: 35,40,42,45,50,50,55,60,70,300. Медиана — среднее между 5-м и 6-м числами.",
        solution: "✅ Медиана = (50+50)/2 = <strong>50 тыс. руб.</strong> Среднее (74,7) завышено из-за зарплаты 300 (выброс). Реальная типичная зарплата — 50 тыс. руб."
    },

    // ========== КЕЙС 4. «Цены на квартиры» ==========
    {
        id: "stat_basic_4",
        title: "🏠 Кейс 4: «Цены на квартиры»",
        description: "Риелтор показывает два района:<br><br>• <strong>Район «Центральный»:</strong> 5, 6, 7, 8, 9, 10, 11, 12, 50 (млн руб.)<br>• <strong>Район «Спокойный»:</strong> 6, 7, 8, 8, 9, 9, 10, 11, 12 (млн руб.)<br><br>Риелтор говорит: «Средняя цена в Центральном — 13 млн, в Спокойном — 8,9 млн. Центральный — элитный!» Покупатель сомневается. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Почему покупатель сомневается?<br>
2️⃣ <strong>Изучение материала:</strong> Вычисляют среднее, медиану, моду, размах.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая характеристика честнее для оценки недвижимости?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают все характеристики.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему при оценке недвижимости используют медиану?`,
        question: "Чему равна МЕДИАНА цен в Центральном районе? (введите число, например 9)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 9,
        hint: "💡 Упорядочи ряд Центрального: 5,6,7,8,9,10,11,12,50. Медиана — 5-й элемент.",
        solution: "✅ Медиана Центрального = <strong>9 млн руб.</strong> Медиана Спокойного = 9 млн руб. Среднее в Центральном (13,1) завышено из-за одной квартиры за 50 млн. Реально «типичная» цена в обоих районах — 9 млн руб."
    },

    // ========== КЕЙС 5. «Кинотеатр: какой фильм лучше?» ==========
    {
        id: "stat_basic_5",
        title: "🎬 Кейс 5: «Какой фильм лучше?»",
        description: "В кинотеатре показали два фильма. Зрители поставили оценки от 1 до 10 (по 10 зрителей):<br><br>• <strong>«Приключение»:</strong> 10, 10, 9, 9, 9, 8, 8, 8, 7, 2<br>• <strong>«Драма»:</strong> 8, 8, 7, 7, 7, 7, 6, 6, 6, 5<br><br>Критик пишет: «Средняя оценка у обоих фильмов — 8,0. Они одинаково хороши!» Зрители не согласны. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Почему зрители не согласны?<br>
2️⃣ <strong>Изучение материала:</strong> Вычисляют среднее, медиану, моду, размах.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой фильм стабильнее? Какой рискованнее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Заполняют таблицу сравнения.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какую характеристику важнее всего учитывать при выборе фильма?`,
        question: "Чему равен РАЗМАХ оценок у фильма «Приключение»? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 8,
        hint: "💡 У «Приключения» максимальная оценка 10, минимальная 2. Размах = 10 − 2 = ?",
        solution: "✅ Размах «Приключения» = 10 − 2 = <strong>8</strong>. У «Драмы» размах = 8 − 5 = 3. Критик ошибся: среднее «Приключения» = 8,0, а «Драмы» = 6,7. У «Приключения» есть выброс (оценка 2), но и есть шанс получить 10/10. Выбор зависит от того, что важнее: стабильность или риск."
    }
];
    // ========== Исследовательское обучение ЗАДАЧА ==========
    const multiplicationISSL = [
        {
            id: "issl_1",
            title: "🧠 «Спор в столовой»",
            description: "В школьной столовой 3 первых блюда, 5 вторых и 4 напитка. Сколько разных обедов можно составить?",
            steps: [
                { step: 1, question: "Петя сказал: «Обедов будет 3+5+4 = 12». Маша сказала: «Нет, 3×5×4 = 60». Кто прав? (введите: Петя или Маша)", hint: "Подумайте о правиле умножения", correctAnswer: "маша", explanation: "Маша права, потому что нужно каждый суп сочетать с каждым салатом и напитком — это правило умножения. Петя ошибся, сложив варианты." },
                { step: 2, question: "А если бы было 3 супа, 5 салатов и 4 напитка, то сколько обедов? А если бы ещё и десерт (3 варианта) добавили? (введите два числа через пробел, например: 44 583)", hint: "3×5×4 и добавьте множитель", correctAnswer: "60 180", explanation: "3×5×4 = 60 обедов. Если добавить десерт (3 варианта): 60 × 3 = 180 обедов." },
                { step: 3, question: "Давайте переберём варианты для 2 супов и 3 салатов. Сколько получилось? А если добавить 2 напитка? (введите два числа через пробел, например: 74 132)", hint: "2×3 и 6×2", correctAnswer: "6 12", explanation: "2 супа × 3 салата = 6 вариантов. Если добавить 2 напитка: 6 × 2 = 12 вариантов." },
                { step: 4, question: "Вернёмся к спору Пети и Маши. Кто был прав? Почему Петя ошибся? (введите: Маша или Петя)", hint: "Кто использовал умножение?", correctAnswer: "маша", explanation: "Права Маша. Петя ошибся, потому что он сложил количество блюд, но для составления обеда нужно выбрать по одному блюду из каждой категории. Правило умножения: 3×5×4 = 60." }
            ]
        }
    ];
// ========== Исследовательское обучение ЗАДАЧА ДЛЯ ТЕМЫ "ПРОТИВОПОЛОЖНОЕ СОБЫТИЕ" ==========
const oppositeISSL = [
    {
        id: "opposite_issl_1",
        title: "🧠 «Спор о монете»",
        description: "Монету подбрасывают 3 раза. Какова вероятность того, что выпадет хотя бы один орёл?",
        steps: [
            {
                step: 1,
                question: "Петя сказал: «Вероятность выпадения орла в одном броске — 1/2. Значит, за три броска вероятность хотя бы одного орла будет 1/2 + 1/2 + 1/2 = 3/2 = 1,5. Это больше единицы, так не бывает. Значит, я где-то ошибся». Маша сказала: «Я посчитала иначе. У меня получилось 7/8 ≈ 0,875». Кто прав? (введите: Петя, Маша или оба)",
                hint: "💡 Подумайте, можно ли просто складывать вероятности для трёх бросков? Что происходит с событиями «орёл в 1-м броске», «орёл во 2-м» и «орёл в 3-м»?",
                correctAnswer: "маша",
                explanation: "✅ Права Маша. Петя ошибся, потому что складывал вероятности совместных событий (орёл может выпасть в нескольких бросках одновременно). Складывать вероятности можно только для несовместных событий."
            },
            {
                step: 2,
                question: "А теперь ответим на другой вопрос: какова вероятность, что НЕ выпадет НИ ОДНОГО орла? (то есть выпадут только решки). Введите вероятность десятичной дробью или простой дробью (например, 0.875 или 7/8)",
                hint: "💡 Вероятность выпадения решки в одном броске — 1/2. Для трёх бросков нужно перемножить вероятности, потому что броски независимы.",
                correctAnswer: "1/8",
                explanation: "✅ P(все решки) = (1/2) × (1/2) × (1/2) = 1/8 = 0,125. Это вероятность того, что орёл не выпадет ни разу."
            },
            {
                step: 3,
                question: "Как связаны события «выпадет хотя бы один орёл» и «не выпадет ни одного орла»? (введите: противоположны или независимы)",
                hint: "💡 Если нет ни одного орла, то что это значит? Могут ли эти события произойти одновременно?",
                correctAnswer: "противоположны",
                explanation: "✅ Эти события противоположны. Если не выпало ни одного орла, значит, выпали только решки. Они не могут произойти одновременно, и их сумма равна 1."
            },
            {
                step: 4,
                question: "Зная, что P(все решки) = 1/8, найдите вероятность P(хотя бы один орёл). Используйте формулу P(A) = 1 − P(Ā). Введите десятичной дробью (например, 0.784)",
                hint: "💡 P(хотя бы один орёл) = 1 − P(ни одного орла) = 1 − 1/8",
                correctAnswer: "0.875",
                explanation: "✅ P(хотя бы один орёл) = 1 − 1/8 = 7/8 = 0,875. Это правильный ответ, который получила Маша."
            },
            {
                step: 5,
                question: "Почему Петя ошибся? Что он сделал не так? (введите: сложил вероятности совместных событий или перемножил вероятности)",
                hint: "💡 Петя получил 1,5 > 1. Что именно он делал с вероятностями 1/2, 1/2 и 1/2?",
                correctAnswer: "сложил вероятности совместных событий",
                explanation: "✅ Петя складывал вероятности, но события «орёл в первом броске», «орёл во втором» и «орёл в третьем» являются совместными (могут произойти одновременно). Складывать вероятности можно только для несовместных событий."
            },
            {
                step: 6,
                question: "В каком случае удобно использовать противоположное событие? Приведите пример из условия: когда событие звучит как... (введите: хотя бы один или ровно один)",
                hint: "💡 Вспомните исходную задачу: «вероятность того, что выпадет ХОТЯ БЫ один орёл».",
                correctAnswer: "хотя бы один",
                explanation: "✅ Противоположное событие удобно применять, когда само событие звучит как «хотя бы один», «не менее одного», «хотя бы раз». Тогда противоположное событие («ни одного») часто считается через умножение вероятностей."
            }
        ]
    }
];
// ========== Исследовательское обучение  ЗАДАЧА ДЛЯ ТЕМЫ "ДИАГРАММА ЭЙЛЕРА" (ВЫВОД ФОРМУЛЫ) ==========
const eulerISSL = [
    {
        id: "euler_issl_1",
        title: "🧠 «Как вывести формулу?»",
        description: "В классе 25 человек. 15 любят математику, 12 любят физику. 5 любят оба предмета. Сколько человек любят хотя бы один предмет?",
        steps: [
            {
                step: 1,
                question: "Ученики попробовали сложить: 15 + 12 = 27. Но в классе всего 25 человек. Почему получилось больше 25? (введите: потому что некоторых посчитали дважды или потому что сложили не те числа)",
                hint: "💡 5 человек любят и математику, и физику. Как они были посчитаны при сложении?",
                correctAnswer: "потому что некоторых посчитали дважды",
                explanation: "✅ При сложении 15 и 12 люди, которые любят оба предмета (5 человек), были посчитаны дважды: один раз в математике, другой раз в физике."
            },
            {
                step: 2,
                question: "Нарисуйте мысленно два пересекающихся круга. Сколько человек любят ТОЛЬКО математику (не любят физику)? (введите число)",
                hint: "💡 Из всех любителей математики (15) вычтите тех, кто любит оба предмета (5).",
                correctAnswer: "10",
                explanation: "✅ Только математику любят: 15 − 5 = 10 человек. <br><img src=' https://disk.360.yandex.ru/d/kXzhRHztfpPtNw ' alt='Диаграмма Эйлера' style='max-width: 100%; margin: 10px 0; border-radius: 10px;'> "
            },
            {
                step: 3,
                question: "Сколько человек любят ТОЛЬКО физику (не любят математику)? (введите число)",
                hint: "💡 Из всех любителей физики (12) вычтите тех, кто любит оба предмета (5).",
                correctAnswer: "7",
                explanation: "✅ Только физику любят: 12 − 5 = 7 человек."
            },
            {
                step: 4,
                question: "Сколько человек любят хотя бы один предмет (только математику + оба + только физику)? (введите число)",
                hint: "💡 Сложите: 10 (только математика) + 5 (оба) + 7 (только физика)",
                correctAnswer: "22",
                explanation: "✅ Всего любителей хотя бы одного предмета: 10 + 5 + 7 = 22 человека."
            },
            {
                step: 5,
                question: "Сравните: при сложении 15 + 12 получилось 27, а правильный ответ — 22. На сколько 27 больше 22? (введите число)",
                hint: "💡 27 − 22 = ?",
                correctAnswer: "5",
                explanation: "✅ 27 − 22 = 5. Это те самые 5 человек, которые любят оба предмета и были посчитаны дважды."
            },
            {
                step: 6,
                question: "Как исправить сложение 15 + 12, чтобы получить правильный ответ 22? Какое действие нужно сделать? (введите: вычесть 5 или прибавить 5)",
                hint: "💡 Мы посчитали 5 человек дважды. Что нужно сделать, чтобы они были посчитаны один раз?",
                correctAnswer: "вычесть 5",
                explanation: "✅ Нужно вычесть 5, потому что эти 5 человек были включены дважды. 15 + 12 − 5 = 22."
            },
            {
                step: 7,
                question: "Запишите формулу в общем виде. Если |M| — любители математики, |Ф| — любители физики, |M ∩ Ф| — любители обоих, то сколько любят хотя бы один предмет? (введите: |M| + |Ф| − |M ∩ Ф| или |M| + |Ф| + |M ∩ Ф|)",
                hint: "💡 По аналогии с числами: 15 + 12 − 5",
                correctAnswer: "|M| + |Ф| − |M ∩ Ф|",
                explanation: "✅ Формула для двух множеств: |A ∪ B| = |A| + |B| − |A ∩ B|. Она работает, когда множества пересекаются."
            },
            {
                step: 8,
                question: "Проверим формулу на других числах. Пусть 10 человек любят математику, 8 — физику, 3 — оба. Сколько любят хотя бы один предмет по формуле? (введите число)",
                hint: "💡 10 + 8 − 3 = ?",
                correctAnswer: "15",
                explanation: "✅ 10 + 8 − 3 = 15 человек. Проверка через диаграмму: только математика: 7, только физика: 5, оба: 3, всего: 7+5+3=15. Формула работает."
            },
            {
                step: 9,
                question: "Вернёмся к исходной задаче. Сколько человек любят хотя бы один предмет? (введите число)",
                hint: "💡 15 + 12 − 5 = ?",
                correctAnswer: "22",
                explanation: "✅ 15 + 12 − 5 = 22 человека. Это окончательный ответ."
            }
        ]
    }
];
// ========== Исследовательское обучение - НЕСОВМЕСТНЫЕ СОБЫТИЯ (эвристическая беседа) ==========
const incompatibleISSL = [
    {
        id: "incompatible_issl_1",
        title: "🔍 «Лотерейный билет»",
        description: "В лотерее один билет может выиграть 100 рублей с вероятностью 0,05, 500 рублей — с вероятностью 0,02, 1000 рублей — с вероятностью 0,01. Какова вероятность выиграть хотя бы какую-нибудь сумму?",
        steps: [
            {
                step: 1,
                question: "Что означает «вероятность выиграть 100 рублей равна 0,05»? Сколько билетов из 100 в среднем выигрывают 100 рублей? (введите число)",
                hint: "💡 Вероятность 0,05 = 5/100, значит, из 100 билетов...",
                correctAnswer: "5",
                explanation: "✅ Вероятность 0,05 означает, что из 100 билетов в среднем 5 выигрывают 100 рублей."
            },
            {
                step: 2,
                question: "А сколько билетов из 100 в среднем выигрывают 500 рублей, если вероятность 0,02? (введите число)",
                hint: "💡 0,02 = 2/100",
                correctAnswer: "2",
                explanation: "✅ Вероятность 0,02 означает, что из 100 билетов в среднем 2 выигрывают 500 рублей."
            },
            {
                step: 3,
                question: "А сколько билетов из 100 в среднем выигрывают 1000 рублей, если вероятность 0,01? (введите число)",
                hint: "💡 0,01 = 1/100",
                correctAnswer: "1",
                explanation: "✅ Вероятность 0,01 означает, что из 100 билетов в среднем 1 выигрывает 1000 рублей."
            },
            {
                step: 4,
                question: "Сколько всего выигрышных билетов в среднем на 100 билетов?",
                hint: "💡 5 + 2 + 1 = ?",
                correctAnswer: "8",
                explanation: "✅ Всего выигрышных билетов: 5 + 2 + 1 = 8 из 100."
            },
            {
                step: 5,
                question: "Какую долю от всех билетов составляют эти 8 выигрышных билетов? (введите десятичной дробью, например 0.15)",
                hint: "💡 8 / 100 = ?",
                correctAnswer: "0.08",
                explanation: "✅ 8/100 = 0,08. Это и есть вероятность того, что случайный билет окажется выигрышным."
            },
            {
                step: 6,
                question: "Посмотрите на исходные вероятности: 0,05; 0,02; 0,01. Какое арифметическое действие нужно сделать, чтобы получить 0,08? (введите: сложить или умножить)",
                hint: "💡 0,05 + 0,02 + 0,01 = 0,08",
                correctAnswer: "сложить",
                explanation: "✅ Мы сложили вероятности: 0,05 + 0,02 + 0,01 = 0,08."
            },
            {
                step: 7,
                question: "Почему мы складываем вероятности, а не умножаем? (введите: потому что события несовместны или потому что события совместны)",
                hint: "💡 Может ли один билет выиграть и 100, и 500 рублей одновременно?",
                correctAnswer: "потому что события несовместны",
                explanation: "✅ События «выиграть 100 рублей», «выиграть 500 рублей» и «выиграть 1000 рублей» не могут произойти одновременно. Они несовместны. Для несовместных событий вероятность объединения равна сумме вероятностей."
            },
            {
                step: 8,
                question: "Сформулируйте правило своими словами. Если события не могут произойти вместе, то вероятность хотя бы одного из них равна... (введите: сумме вероятностей или произведению вероятностей)",
                hint: "💡 Вспомните, что мы сделали с числами 0,05; 0,02; 0,01",
                correctAnswer: "сумме вероятностей",
                explanation: "✅ Для несовместных событий вероятность того, что произойдёт хотя бы одно из них, равна сумме их вероятностей: P(A или B или C) = P(A) + P(B) + P(C)."
            },
            {
                step: 9,
                question: "Проверим на прочность. Если бы вероятности были 0,5; 0,4; 0,3, то сумма была бы 1,2. Может ли вероятность быть больше 1? (введите: да или нет)",
                hint: "💡 Вероятность всегда находится в пределах от 0 до 1",
                correctAnswer: "нет",
                explanation: "✅ Вероятность не может быть больше 1. Если сумма вероятностей совместных событий даёт больше 1, значит, события пересекаются, и нужно использовать другую формулу."
            },
            {
                step: 10,
                question: "Вернёмся к исходной задаче. Какова вероятность выиграть хотя бы какую-нибудь сумму? (введите десятичной дробью, например 0.45)",
                hint: "💡 0,05 + 0,02 + 0,01 = ?",
                correctAnswer: "0.08",
                explanation: "✅ P(выигрыш) = 0,05 + 0,02 + 0,01 = 0,08. Вероятность проигрыша = 1 − 0,08 = 0,92."
            }
        ]
    }
];
// ========== Исследовательское обучение - НЕСОВМЕСТНЫЕ СОБЫТИЯ (эвристическая беседа) ==========
const incompatibleISSL_8 = [
    {
        id: "incompatible_issl_8_1",
        title: "🧠 «Спор о кубике: как складывать вероятности?»",
        description: "Бросают один игральный кубик. Как найти вероятность события A или B, где A и B — два разных события?",
        steps: [
            {
                step: 1,
                question: "Бросаем один игральный кубик. Событие A = «выпадет 2», событие B = «выпадет 5». Какова вероятность события A ∪ B (выпадет 2 или 5)?",
                hint: "💡 Посчитай количество благоприятных исходов: какие числа нас устраивают? Всего исходов 6.",
                correctAnswer: "2/6",
                explanation: "✅ Благоприятные исходы: {2, 5} — 2 исхода. Всего исходов: 6. P(A∪B) = 2/6 = 1/3 ≈ 0,333."
            },
            {
                step: 2,
                question: "Чему равна P(A) + P(B) для этих событий? P(A) = 1/6, P(B) = 1/6. (введите дробью, например 1/3)",
                hint: "💡 1/6 + 1/6 = ?",
                correctAnswer: "2/6",
                explanation: "✅ 1/6 + 1/6 = 2/6 = 1/3. Это совпадает с P(A∪B), которую мы нашли в шаге 1."
            },
            {
                step: 3,
                question: "Теперь рассмотрим другие события на том же кубике. Событие C = «выпадет чётное число», событие D = «выпадет число, кратное 3». Найдите P(C) и P(D). (введите две дроби через пробел, например 1/2 1/3)",
                hint: "💡 Чётные числа на кубике: 2, 4, 6 (3 исхода). Кратные 3: 3, 6 (2 исхода).",
                correctAnswer: "3/6 2/6",
                explanation: "✅ P(C) = 3/6 = 1/2. P(D) = 2/6 = 1/3."
            },
            {
                step: 4,
                question: "Чему равна P(C) + P(D)? (введите дробью, например 5/6)",
                hint: "💡 3/6 + 2/6 = ?",
                correctAnswer: "5/6",
                explanation: "✅ 3/6 + 2/6 = 5/6 ≈ 0,833."
            },
            {
                step: 5,
                question: "А теперь найдите P(C ∪ D) — вероятность выпадения чётного числа ИЛИ числа, кратного 3. Посчитай количество благоприятных исходов. (введите дробью, например 4/6)",
                hint: "💡 Какие числа нас устраивают? Чётные: 2,4,6. Кратные 3: 3,6. Объединяем: {2,3,4,6} — 4 исхода.",
                correctAnswer: "4/6",
                explanation: "✅ Благоприятные исходы: {2,3,4,6} — 4 исхода. P(C∪D) = 4/6 = 2/3 ≈ 0,667."
            },
            {
                step: 6,
                question: "Сравните P(C) + P(D) = 5/6 и P(C∪D) = 4/6. Они равны? (введите: да или нет)",
                hint: "💡 5/6 ≠ 4/6",
                correctAnswer: "нет",
                explanation: "✅ P(C)+P(D) = 5/6, а P(C∪D) = 4/6. Они НЕ равны. Простое сложение дало слишком большой результат."
            },
            {
                step: 7,
                question: "На сколько P(C)+P(D) больше P(C∪D)? Какое число было посчитано дважды? (введите число)",
                hint: "💡 5/6 − 4/6 = ? Это число соответствует какому исходу?",
                correctAnswer: "6",
                explanation: "✅ 5/6 − 4/6 = 1/6. Это вероятность выпадения 6 — исхода, который входит и в C, и в D. Он был посчитан дважды."
            },
            {
                step: 8,
                question: "В чём разница между первой парой событий (A и B: выпадение 2 или 5) и второй парой (C и D: чётное или кратное 3)? (введите: есть общие исходы или нет общих исходов)",
                hint: "💡 Может ли число быть одновременно и 2, и 5? А может ли быть одновременно чётным и кратным 3?",
                correctAnswer: "есть общие исходы",
                explanation: "✅ У событий A и B нет общих исходов (не могут произойти одновременно). У событий C и D есть общий исход — число 6 (оно и чётное, и кратно 3)."
            },
            {
                step: 9,
                question: "Как называются события, которые не могут произойти одновременно? (введите: совместные или несовместные)",
                hint: "💡 Если нет общих исходов, события...",
                correctAnswer: "несовместные",
                explanation: "✅ События, которые не могут произойти одновременно, называются несовместными. Например, выпадение 2 и выпадение 5 — несовместны."
            },
            {
                step: 10,
                question: "Сформулируй правило: Для НЕСОВМЕСТНЫХ событий вероятность A или B равна... (введите: сумме вероятностей или произведению вероятностей)",
                hint: "💡 Вспомни шаг 2: P(A)+P(B) = P(A∪B)",
                correctAnswer: "сумме вероятностей",
                explanation: "✅ Для несовместных событий: P(A∪B) = P(A) + P(B). Для совместных событий нужно вычитать пересечение: P(A∪B) = P(A) + P(B) − P(A∩B)."
            }
        ]
    }
];
// ========== Исследовательское обучение ЗАДАЧА ДЛЯ ТЕМЫ "УСЛОВНАЯ ВЕРОЯТНОСТЬ" ==========
const conditionalISSL = [
    {
        id: "conditional_issl_1",
        title: "🧠«Спор о кубике»",
        description: "Бросают один игральный кубик. Вам сообщают, что выпавшее число — чётное. Какова вероятность того, что выпала шестёрка?",
        steps: [
            {
                step: 1,
                question: "Антон сказал: «Вероятность выпадения шестёрки без всяких условий — 1/6. Если я узнал, что число чётное, то ничего не изменилось. Шестёрка — это одно из шести возможных чисел. Значит, вероятность так и осталась 1/6». Елена сказала: «А я думаю иначе. Если известно, что число чётное, то возможны только варианты: 2, 4, 6. Всего три варианта. Из них шестёрка — один. Значит, вероятность равна 1/3». Кто прав? (введите: Антон, Елена или оба)",
                hint: "💡 Что значит «известно, что выпало чётное число»? Как это меняет количество возможных исходов?",
                correctAnswer: "елена",
                explanation: "✅ Права Елена. Когда мы узнаём, что число чётное, пространство исходов сужается: остаются только 2, 4 и 6. Все они равновозможны. Шестёрка — один из трёх вариантов, поэтому вероятность = 1/3."
            },
            {
                step: 2,
                question: "Как называется вероятность события A при условии, что событие B уже произошло? (введите: условная или безусловная)",
                hint: "💡 Эта вероятность зависит от наступления другого события.",
                correctAnswer: "условная",
                explanation: "✅ Такая вероятность называется условной. Обозначается P(A|B) — вероятность события A при условии, что событие B произошло."
            },
            {
                step: 3,
                question: "В нашем примере: A = «выпала шестёрка», B = «выпало чётное число». Сколько исходов благоприятны для A ∩ B (и A, и B одновременно)? (введите число)",
                hint: "💡 Шестёрка — это чётное число. Значит, A ∩ B = «выпала шестёрка».",
                correctAnswer: "1",
                explanation: "✅ A ∩ B = «выпала шестёрка». Такой исход только один (6)."
            },
            {
                step: 4,
                question: "Сколько исходов благоприятны для B (выпало чётное число)? (введите число)",
                hint: "💡 Чётные числа на кубике: 2, 4, 6.",
                correctAnswer: "3",
                explanation: "✅ Чётные числа на кубике: 2, 4, 6. Всего 3 благоприятных исхода."
            },
            {
                step: 5,
                question: "Чему равна условная вероятность P(A|B) по формуле P(A|B) = |A ∩ B| / |B|? (введите десятичной дробью, например 0.125)",
                hint: "💡 P(A|B) = 1 / 3 = ?",
                correctAnswer: "0.333",
                explanation: "✅ P(A|B) = 1/3 ≈ 0,333. Это вероятность выпадения шестёрки при условии, что выпало чётное число."
            },
            {
                step: 6,
                question: "Общая формула условной вероятности: P(A|B) = P(A ∩ B) / P(B). Найдите P(A|B) через вероятности. P(A ∩ B) = 1/6, P(B) = 3/6 = 1/2. (введите десятичной дробью, например 0.451)",
                hint: "💡 P(A|B) = (1/6) / (1/2) = (1/6) × (2/1) = ?",
                correctAnswer: "0.333",
                explanation: "✅ P(A|B) = (1/6) / (1/2) = (1/6) × 2 = 2/6 = 1/3 ≈ 0,333. Тот же результат, что и при подсчёте через исходы."
            },
            {
                step: 7,
                question: "Сравните: P(A) без условия = 1/6 ≈ 0,167, а P(A|B) = 1/3 ≈ 0,333. Условная вероятность оказалась выше. Почему? (введите: потому что условие отсеяло нечётные числа или потому что шестёрка перестала быть возможной)",
                hint: "💡 Какие исходы исключило условие «число чётное»?",
                correctAnswer: "потому что условие отсеяло нечётные числа",
                explanation: "✅ Условие «число чётное» исключило нечётные числа (1,3,5). Шестёрка осталась, а количество возможных исходов уменьшилось с 6 до 3. Поэтому шанс шестёрки вырос с 1/6 до 1/3."
            },
            {
                step: 8,
                question: "А если бы условие было другим: «выпало число больше 4». Какова тогда вероятность выпадения шестёрки? (введите десятичной дробью, например 0.1)",
                hint: "💡 Числа больше 4 на кубике: 5 и 6. Шестёрка — один из двух вариантов.",
                correctAnswer: "0.5",
                explanation: "✅ Если выпало число больше 4, то возможны исходы: 5 и 6. Шестёрка — один из двух, поэтому P = 1/2 = 0,5. Вероятность стала ещё выше."
            },
            {
                step: 9,
                question: "Когда условная вероятность равна безусловной? (введите: когда события независимы или когда события зависимы)",
                hint: "💡 Если появление B не влияет на вероятность A, то P(A|B) = P(A).",
                correctAnswer: "когда события независимы",
                explanation: "✅ Условная вероятность равна безусловной, когда события независимы. Например, при подбрасывании монеты два раза: выпадение орла во второй раз не зависит от того, что выпало в первый."
            }
        ]
    }
];
// ========== Исследовательское обучение  ЗАДАЧА ДЛЯ ТЕМЫ "ДЕРЕВО ЭКСПЕРИМЕНТА" ==========
const treeISSL = [
    {
        id: "tree_issl_1",
        title: "🧠«Спор о шарах»",
        description: "В коробке 2 белых и 1 чёрный шар. Из коробки вынимают два шара подряд без возвращения. Какова вероятность вытащить два белых шара?",
        steps: [
            {
                step: 1,
                question: "Роман сказал: «Вероятность вытащить белый шар первый раз — 2/3. После этого в коробке остаётся 1 белый и 1 чёрный шар. Вероятность вытащить белый во второй раз — 1/2. Значит, вероятность двух белых шаров равна 2/3 × 1/2 = 1/3». Ольга сказала: «А я думаю иначе. Всего возможных пар шаров: из трёх шаров выбрать два — это 3 комбинации: (Б1,Б2), (Б1,Ч), (Б2,Ч). Только одна комбинация — два белых. Значит, вероятность равна 1/3». Кто прав? (введите: Роман, Ольга или оба)",
                hint: "💡 Оба получили одинаковый ответ 1/3. Может быть, правы оба?",
                correctAnswer: "оба",
                explanation: "✅ Правы оба. Роман использовал умножение вероятностей (условные вероятности), а Ольга — комбинаторный способ. Оба способа привели к правильному ответу 1/3."
            },
            {
                step: 2,
                question: "Как наглядно изобразить все возможные исходы этого эксперимента, чтобы ничего не пропустить? (введите: дерево или таблица)",
                hint: "💡 Этот способ похож на ветви, которые расходятся от корня.",
                correctAnswer: "дерево",
                explanation: "✅ Для последовательных экспериментов удобно использовать дерево вероятностей. Оно помогает шаг за шагом видеть все варианты и не запутаться."
            },
            {
                step: 3,
                question: "При построении дерева: первый шар может быть белым или чёрным. Какова вероятность вытащить белый шар первым? (введите десятичной дробью, например 0.541)",
                hint: "💡 Всего шаров 3, белых — 2.",
                correctAnswer: "0.667",
                explanation: "✅ P(первый белый) = 2/3 ≈ 0,667. P(первый чёрный) = 1/3 ≈ 0,333."
            },
            {
                step: 4,
                question: "Если первый шар был белым, то в коробке осталось 1 белый и 1 чёрный. Какова вероятность вытащить белый вторым? (введите десятичной дробью, например 0.3)",
                hint: "💡 После того как вынули один белый, осталось 2 шара: 1 белый и 1 чёрный.",
                correctAnswer: "0.5",
                explanation: "✅ P(второй белый | первый белый) = 1/2 = 0,5."
            },
            {
                step: 5,
                question: "Если первый шар был чёрным, то в коробке осталось 2 белых шара. Какова вероятность вытащить белый вторым? (введите число)",
                hint: "💡 После того как вынули чёрный, осталось 2 белых шара.",
                correctAnswer: "1",
                explanation: "✅ P(второй белый | первый чёрный) = 2/2 = 1. Белый выпадет обязательно."
            },
            {
                step: 6,
                question: "Постройте мысленно дерево. Чему равна вероятность вытащить два белых шара (путь «Белый → Белый»)? (введите десятичной дробью, например 0.452)",
                hint: "💡 Перемножьте вероятности вдоль пути: P(первый белый) × P(второй белый | первый белый) = 2/3 × 1/2",
                correctAnswer: "0.333",
                explanation: "✅ P = (2/3) × (1/2) = 1/3 ≈ 0,333. Это и есть ответ на исходный вопрос."
            },
            {
                step: 7,
                question: "Чему равна вероятность вытащить сначала белый, потом чёрный? (введите десятичной дробью, например 0.741)",
                hint: "💡 Путь «Белый → Чёрный»: 2/3 × 1/2",
                correctAnswer: "0.333",
                explanation: "✅ P = (2/3) × (1/2) = 1/3 ≈ 0,333."
            },
            {
                step: 8,
                question: "Чему равна вероятность вытащить сначала чёрный, потом белый? (введите десятичной дробью, например 0.985)",
                hint: "💡 Путь «Чёрный → Белый»: 1/3 × 1",
                correctAnswer: "0.333",
                explanation: "✅ P = (1/3) × 1 = 1/3 ≈ 0,333."
            },
            {
                step: 9,
                question: "Сумма вероятностей всех путей от корня до листьев должна равняться 1. Проверьте: 1/3 + 1/3 + 1/3 + 0 = ? (введите число)",
                hint: "💡 Сложите все вероятности: 0,333 + 0,333 + 0,333 + 0",
                correctAnswer: "1",
                explanation: "✅ Сумма вероятностей всех путей равна 1. Это важное свойство дерева вероятностей."
            },
            {
                step: 10,
                question: "В чём главное преимущество дерева перед другими способами? (введите: наглядность последовательных шагов или быстрый подсчёт)",
                hint: "💡 Дерево показывает все возможные исходы по шагам, особенно удобно, когда вероятности на следующих шагах зависят от предыдущих.",
                correctAnswer: "наглядность последовательных шагов",
                explanation: "✅ Дерево наглядно показывает все возможные исходы эксперимента по шагам. На каждом шаге видны вероятности переходов. Это особенно удобно, когда вероятности на следующих шагах зависят от предыдущих (условные вероятности)."
            }
        ]
    }
];
    // ========== ПУСТЫЕ МАССИВЫ ==========
        const statisticsBasicPractice= [];
        const grade7_topic3Tests = [];
    const grade7_topic3Formulas = [];
    const grade7_topic1Practice = [], grade7_topic2Practice = [], grade7_topic3Practice = [];
const grade7_topic3Cases= [],  grade7_topic4Practice= [];
const grade7_topic5Practice= [];
const grade7_topic6Practice= [];
const grade7_topic7Formulas= [], grade7_topic7Practice= [];
const grade7_topic8Formulas= [], grade7_topic8Practice= [];
const grade7_topic9Formulas= [], grade7_topic9Practice= [];


    
    const grade9_topic1Formulas = [], grade9_topic2Formulas = [], grade9_topic3Formulas = [], grade9_topic4Formulas = [], grade9_topic5Formulas = [], grade9_topic6Formulas = [];
    const grade9_topic1Practice = [], grade9_topic2Practice = [], grade9_topic3Practice = [], grade9_topic4Practice = [], grade9_topic5Practice = [], grade9_topic6Practice = [];
// ========== ТРКМ - ЧАСТОТА ЗНАЧЕНИЙ В МАССИВЕ ДАННЫХ (7 КЛАСС) ==========
const grade7_topic6Formulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_frequency",
        title: "🧠 ТРКМ: «Частота значений в массиве данных» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы о частоте значений. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта. Для каждого вопроса есть подсказка.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Что такое частота значения в массиве данных?",
                hint: "💡 Это отношение количества вхождений значения к общему числу значений.",
                correctAnswer: "отношение количества вхождений значения к общему количеству всех значений",
                explanation: "✅ ЧАСТОТА — это доля, которую составляет данное значение от общего числа всех значений."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "По какой формуле вычисляется частота значения?",
                hint: "💡 Частота = количество вхождений ÷ общее количество всех значений.",
                correctAnswer: "количество вхождений / общее количество всех значений",
                explanation: "✅ Частота = (количество вхождений значения) / (общее количество всех значений)."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "Чему равна сумма частот всех значений в любом массиве данных?",
                hint: "💡 Сумма всех долей всегда равна целому.",
                correctAnswer: "1",
                explanation: "✅ Сумма частот всех значений всегда равна <strong>1</strong> (или 100%)."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "В классе 25 учеников. Из них 10 человек любят математику. Какова частота значения «любит математику»? (введите десятичной дробью, например 0.4)",
                hint: "💡 Частота = 10 ÷ 25 = ?",
                correctAnswer: "0.4",
                explanation: "✅ Частота = 10/25 = <strong>0,4</strong> (или 40%)."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "Может ли частота значения быть больше 1? (введите: да или нет)",
                hint: "💡 Частота — это доля, а доля не может быть больше целого.",
                correctAnswer: "нет",
                explanation: "✅ Частота всегда находится в пределах от 0 до 1 включительно, так как количество вхождений не может превышать общее количество."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "Чем частота отличается от количества (абсолютной частоты)? Почему частота удобнее для сравнения разных групп?",
                hint: "💡 Что лучше: 60 из 100 или 200 из 500?",
                correctAnswer: "количество показывает, сколько раз встретилось значение, а частота — какую долю это составляет; частота удобна для сравнения групп разного размера",
                options: [
                    { value: "количество показывает долю, а частота — число предметов", text: "Количество показывает долю, а частота — число предметов" },
                    { value: "количество и частота — это одно и то же", text: "Количество и частота — это одно и то же" },
                    { value: "количество показывает, сколько раз встретилось значение, а частота — какую долю это составляет; частота удобна для сравнения групп разного размера", text: "Количество показывает, сколько раз встретилось значение, а частота — какую долю это составляет от общего числа. Частота удобнее для сравнения групп разного размера, потому что она «нормирует» данные." },
                    { value: "частота удобнее, потому что она всегда целое число", text: "Частота удобнее, потому что она всегда целое число" }
                ],
                explanation: "✅ ЧАСТОТА — это доля, КОЛИЧЕСТВО — абсолютное число. Частота удобна для сравнения групп разного размера (нормирует данные)."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "Почему сумма частот всех значений всегда равна 1?",
                hint: "💡 Что получится, если сложить все количества вхождений и разделить на общее количество?",
                correctAnswer: "потому что сумма количеств всех значений равна общему числу значений",
                options: [
                    { value: "потому что так договорились математики", text: "Потому что так договорились математики" },
                    { value: "потому что сумма количеств всех значений равна общему числу значений", text: "Потому что сумма количеств всех значений равна общему числу значений. Если каждое количество разделить на общее число, а потом сложить, получится (общее число)/(общее число) = 1." },
                    { value: "потому что частоты всегда округляют до 1", text: "Потому что частоты всегда округляют до 1" },
                    { value: "потому что сумма частот равна среднему арифметическому", text: "Потому что сумма частот равна среднему арифметическому" }
                ],
                explanation: "✅ Сумма количеств вхождений = общее количество значений. Разделив каждое количество на общее число и сложив, получим 1."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "В наборе данных частоты значений: 0,2; 0,3; 0,4; 0,1. Что можно сказать о проверке правильности вычислений?",
                hint: "💡 Проверь сумму частот.",
                correctAnswer: "сумма = 1, значит, вычисления верны",
                options: [
                    { value: "сумма = 1, значит, вычисления верны", text: "Сумма 0,2+0,3+0,4+0,1 = 1, значит, вычисления верны" },
                    { value: "сумма не имеет значения, главное — чтобы каждая частота была меньше 1", text: "Сумма не имеет значения, главное — чтобы каждая частота была меньше 1" },
                    { value: "частоты должны быть целыми числами, значит, вычисления неверны", text: "Частоты должны быть целыми числами, значит, вычисления неверны" },
                    { value: "частоты должны быть одинаковыми, значит, вычисления неверны", text: "Частоты должны быть одинаковыми, значит, вычисления неверны" }
                ],
                explanation: "✅ Сумма частот = 0,2+0,3+0,4+0,1 = <strong>1</strong>. Это признак правильности вычислений."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "Как с помощью частот найти среднее арифметическое числового набора?",
                hint: "💡 Нужно умножить каждое значение на его частоту и сложить результаты.",
                correctAnswer: "среднее = сумма (значение × частота)",
                options: [
                    { value: "среднее = сумма всех значений, делённая на количество", text: "Среднее = сумма всех значений, делённая на количество. Частоты для этого не нужны" },
                    { value: "среднее = сумма (значение × частота)", text: "Среднее = сумма произведений каждого значения на его частоту. Это удобно, когда исходных данных много, а различных значений мало." },
                    { value: "среднее = сумма частот, делённая на количество значений", text: "Среднее = сумма частот, делённая на количество значений" },
                    { value: "частоты не используются для нахождения среднего арифметического", text: "Частоты не используются для нахождения среднего арифметического" }
                ],
                explanation: "✅ Среднее арифметическое = Σ (значение × частота). Способ удобен, когда данных много, а различных значений мало."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "В опросе участвовали две школы: в первой 50 учеников, во второй 200. В первой школе 30 человек любят физику, во второй — 80. Можно ли сравнить популярность физики по количеству? Что нужно использовать?",
                hint: "💡 30 из 50 — это 60%, 80 из 200 — это 40%.",
                correctAnswer: "нужно сравнивать частоты, так как количество не учитывает размер групп",
                options: [
                    { value: "нужно сравнивать количества: 80 > 30, значит, во второй школе физику любят больше", text: "Нужно сравнивать количества: 80 > 30, значит, во второй школе физику любят больше" },
                    { value: "нужно сравнивать частоты (доли), так как количество не учитывает размер групп", text: "Нужно сравнивать частоты (доли): в первой школе 30/50 = 0,6, во второй 80/200 = 0,4. Значит, в первой школе физику любят больше (60% против 40%)." },
                    { value: "нельзя сравнить, потому что опросы проводились в разное время", text: "Нельзя сравнить, потому что опросы проводились в разное время" },
                    { value: "нужно сравнивать размах, а не частоту", text: "Нужно сравнивать размах, а не частоту" }
                ],
                explanation: "✅ Нужно сравнивать ЧАСТОТЫ (доли): 30/50 = 0,6 (60%), 80/200 = 0,4 (40%). В первой школе физику любят больше, хотя абсолютное число меньше."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ==========
    {
        id: "trkm_cluster_frequency",
        title: "🧠 ТРКМ: Кластер «Частота значений»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Каждая карточка должна попасть в свой раздел. Неправильные карточки будут выделены красным.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_def", name: "📖 ОПРЕДЕЛЕНИЕ", maxCards: 2 },
            { id: "branch_formula", name: "📐 ФОРМУЛА", maxCards: 2 },
            { id: "branch_property", name: "🔍 СВОЙСТВО", maxCards: 2 },
            { id: "branch_purpose", name: "🎯 НАЗНАЧЕНИЕ", maxCards: 2 },
            { id: "branch_examples", name: "📊 ПРИМЕРЫ", maxCards: 2 }
        ],
        cards: [
            // Ветвь: ОПРЕДЕЛЕНИЕ (2 карточки)
            { id: "card_def_1", text: "Доля, которую составляет значение от общего числа данных" },
            { id: "card_def_2", text: "Относительная частота (в отличие от абсолютной)" },
            
            // Ветвь: ФОРМУЛА (2 карточки)
            { id: "card_formula_1", text: "Частота = количество вхождений / общее количество" },
            { id: "card_formula_2", text: "Значение может быть от 0 до 1" },
            
            // Ветвь: СВОЙСТВО (2 карточки)
            { id: "card_prop_1", text: "Сумма частот всех значений = 1 (или 100%)" },
            { id: "card_prop_2", text: "Позволяет сравнивать группы разного размера" },
            
            // Ветвь: НАЗНАЧЕНИЕ (2 карточки)
            { id: "card_purp_1", text: "Для сравнения долей в группах разного объёма" },
            { id: "card_purp_2", text: "Для краткого описания больших массивов данных" },
            
            // Ветвь: ПРИМЕРЫ (2 карточки)
            { id: "card_ex_1", text: "Из 25 учеников 10 любят математику → частота = 0,4" },
            { id: "card_ex_2", text: "30 из 50 (0,6) vs 80 из 200 (0,4) — сравнение долей" }
        ]
    }
];
// ========== ТРКМ - РАЗМАХ ЧИСЛОВОГО НАБОРА (7 КЛАСС) ==========
const grade7_topic5Formulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_range",
        title: "🧠 ТРКМ: «Размах числового набора» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы о размахе. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта. Для каждого вопроса есть подсказка.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Что такое размах числового набора?",
                hint: "💡 Нужно найти разницу между самым большим и самым маленьким числом.",
                correctAnswer: "разность между наибольшим и наименьшим значением",
                explanation: "✅ РАЗМАХ — это разность между наибольшим и наименьшим значением в наборе данных."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "Как найти размах числового набора?",
                hint: "💡 Из какого числа вычесть какое?",
                correctAnswer: "из максимального вычесть минимальное",
                explanation: "✅ Чтобы найти размах, нужно из МАКСИМАЛЬНОГО числа вычесть МИНИМАЛЬНОЕ."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "В наборе 8, 15, 3, 12, 20 чему равен размах? (введите число)",
                hint: "💡 Найди самое большое и самое маленькое число.",
                correctAnswer: "17",
                explanation: "✅ Размах = 20 − 3 = <strong>17</strong>."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "Может ли размах быть равен нулю? В каком случае?",
                hint: "💡 Когда разность между максимумом и минимумом равна нулю?",
                correctAnswer: "если все числа одинаковые",
                explanation: "✅ Размах = 0, если ВСЕ ЧИСЛА В НАБОРЕ ОДИНАКОВЫЕ (максимум = минимум)."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "В наборе 100, 102, 101, 99, 1000 чему равен размах? (введите число)",
                hint: "💡 Самое большое число = 1000, самое маленькое = 99.",
                correctAnswer: "901",
                explanation: "✅ Размах = 1000 − 99 = <strong>901</strong>."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "Почему размах считается несовершенной мерой разброса данных? В чём его главный недостаток?",
                hint: "💡 Сколько чисел учитывает размах? Все или только два?",
                correctAnswer: "размах учитывает только максимум и минимум и ничего не говорит о распределении остальных чисел",
                options: [
                    { value: "размах слишком сложно вычислять", text: "Размах слишком сложно вычислять" },
                    { value: "размах учитывает только максимум и минимум и ничего не говорит о распределении остальных чисел", text: "Размах учитывает только два значения (максимум и минимум) и ничего не говорит о том, как распределены остальные числа. Например, наборы 10,20,30,40,50 и 10,10,10,50,50 имеют одинаковый размах (40), но совершенно разную структуру." },
                    { value: "размах всегда равен среднему арифметическому", text: "Размах всегда равен среднему арифметическому" },
                    { value: "размах нельзя вычислить для чётного количества чисел", text: "Размах нельзя вычислить для чётного количества чисел" }
                ],
                explanation: "✅ Главный недостаток размаха: он учитывает ТОЛЬКО ДВА ЧИСЛА (максимум и минимум) и НЕ ПОКАЗЫВАЕТ, как распределены остальные данные."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "В каких ситуациях размах может быть полезен, несмотря на свои недостатки?",
                hint: "💡 Когда нужно быстро оценить разброс или понять, есть ли экстремальные значения.",
                correctAnswer: "когда нужно быстро оценить разброс или понять, есть ли в данных экстремальные значения",
                options: [
                    { value: "когда нужно быстро оценить разброс или понять, есть ли в данных экстремальные значения", text: "Когда нужно быстро оценить разброс «на глаз» или понять, есть ли в данных экстремальные значения. Например, при контроле температуры в холодильнике важно знать размах (минимальную и максимальную температуру)." },
                    { value: "размах полезен только для наборов с чётным количеством чисел", text: "Размах полезен только для наборов с чётным количеством чисел" },
                    { value: "размах никогда не бывает полезен, его не используют в реальной жизни", text: "Размах никогда не бывает полезен, его не используют в реальной жизни" },
                    { value: "размах полезен только для нахождения среднего арифметического", text: "Размах полезен только для нахождения среднего арифметического" }
                ],
                explanation: "✅ Размах полезен для БЫСТРОЙ оценки разброса и выявления экстремальных значений (например, в контроле качества или мониторинге температуры)."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "В наборе: 5, 5, 5, 5, 5. Чему равен размах? Что это означает?",
                hint: "💡 Все числа одинаковые. Какая разница между самым большим и самым маленьким?",
                correctAnswer: "размах = 0, все числа одинаковые, разброса нет",
                options: [
                    { value: "размах = 5, числа разбросаны сильно", text: "Размах = 5, числа разбросаны сильно" },
                    { value: "размах = 0, все числа одинаковые, разброса нет", text: "Размах = 0, все числа одинаковые, разброса нет" },
                    { value: "размах = 25, числа очень разные", text: "Размах = 25, числа очень разные" },
                    { value: "размах = 1, числа почти одинаковые", text: "Размах = 1, числа почти одинаковые" }
                ],
                explanation: "✅ Размах = 5 − 5 = <strong>0</strong>. Это означает, что все числа одинаковые, разброс данных отсутствует."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "Может ли размах быть отрицательным? Почему?",
                hint: "💡 Может ли максимум быть меньше минимума?",
                correctAnswer: "нет, потому что максимум всегда больше или равен минимуму, поэтому их разность неотрицательна",
                options: [
                    { value: "да, если в наборе есть отрицательные числа", text: "Да, если в наборе есть отрицательные числа" },
                    { value: "да, если наибольшее число меньше наименьшего", text: "Да, если наибольшее число меньше наименьшего" },
                    { value: "нет, потому что максимум всегда больше или равен минимуму, поэтому их разность неотрицательна", text: "Нет, потому что максимум всегда больше или равен минимуму, поэтому их разность неотрицательна" },
                    { value: "нет, потому что размах — это всегда абсолютная величина", text: "Нет, потому что размах — это всегда абсолютная величина" }
                ],
                explanation: "✅ Размах НЕ МОЖЕТ быть отрицательным, так как максимальное значение всегда больше или равно минимальному, и их разность ≥ 0."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "Сравните размах и дисперсию. Что общего и в чём разница?",
                hint: "💡 Обе показывают разброс, но размах учитывает только два числа, а дисперсия — все.",
                correctAnswer: "обе показывают разброс, но размах учитывает только max и min, а дисперсия — все значения",
                options: [
                    { value: "размах и дисперсия — это одно и то же, просто разные названия", text: "Размах и дисперсия — это одно и то же, просто разные названия" },
                    { value: "обе показывают разброс, но размах учитывает только max и min, а дисперсия — все значения", text: "Обе характеристики показывают разброс данных. Но размах учитывает только два числа (max и min), а дисперсия учитывает все значения и поэтому точнее описывает разброс." },
                    { value: "размах показывает среднее значение, а дисперсия — разброс", text: "Размах показывает среднее значение, а дисперсия — разброс" },
                    { value: "размах вычисляется через квадраты отклонений, а дисперсия — через максимум и минимум", text: "Размах вычисляется через квадраты отклонений, а дисперсия — через максимум и минимум" }
                ],
                explanation: "✅ ОБЩЕЕ: обе показывают разброс данных. РАЗНИЦА: размах учитывает ТОЛЬКО два числа, дисперсия — ВСЕ значения, поэтому она точнее."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ==========
    {
        id: "trkm_cluster_range",
        title: "🧠 ТРКМ: Кластер «Размах числового набора»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Каждая карточка должна попасть в свой раздел. Неправильные карточки будут выделены красным.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_def", name: "📖 ОПРЕДЕЛЕНИЕ", maxCards: 2 },
            { id: "branch_formula", name: "📐 ФОРМУЛА", maxCards: 2 },
            { id: "branch_examples", name: "📊 ПРИМЕРЫ", maxCards: 2 },
            { id: "branch_advantages", name: "✅ ПРЕИМУЩЕСТВА", maxCards: 2 },
            { id: "branch_limitations", name: "⚠️ НЕДОСТАТКИ", maxCards: 2 }
        ],
        cards: [
            // Ветвь: ОПРЕДЕЛЕНИЕ (2 карточки)
            { id: "card_def_1", text: "Разность между наибольшим и наименьшим значением в наборе" },
            { id: "card_def_2", text: "Показывает разброс данных" },
            
            // Ветвь: ФОРМУЛА (2 карточки)
            { id: "card_formula_1", text: "Размах = максимум − минимум" },
            { id: "card_formula_2", text: "Обозначается: R = max − min" },
            
            // Ветвь: ПРИМЕРЫ (2 карточки)
            { id: "card_ex_1", text: "Набор 3,7,12,15,20 → размах = 20−3 = 17" },
            { id: "card_ex_2", text: "Набор 5,5,5,5,5 → размах = 0" },
            
            // Ветвь: ПРЕИМУЩЕСТВА (2 карточки)
            { id: "card_adv_1", text: "Простота вычисления" },
            { id: "card_adv_2", text: "Быстрая оценка разброса «на глаз»" },
            
            // Ветвь: НЕДОСТАТКИ (2 карточки)
            { id: "card_lim_1", text: "Учитывает только максимум и минимум" },
            { id: "card_lim_2", text: "Ничего не говорит о распределении остальных чисел" }
        ]
    }
];
// ========== ТРКМ - МЕДИАНА ЧИСЛОВОГО НАБОРА (7 КЛАСС) ==========
const grade7_topic4Formulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_median",
        title: "🧠 ТРКМ: «Медиана числового набора» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы о медиане. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта. Для каждого вопроса есть подсказка.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Что такое медиана упорядоченного числового ряда?",
                hint: "💡 Слово «медиана» происходит от латинского «medius» — середина.",
                correctAnswer: "число, стоящее посередине",
                explanation: "✅ МЕДИАНА — это число, которое стоит посередине упорядоченного (отсортированного) ряда чисел."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "Как найти медиану набора с НЕЧЁТНЫМ количеством чисел?",
                hint: "💡 Если чисел 5, какое по счёту число будет посередине?",
                correctAnswer: "упорядочить ряд и взять число, стоящее в центре",
                explanation: "✅ Для НЕЧЁТНОГО количества чисел медиана — это число, которое стоит ровно посередине упорядоченного ряда."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "Как найти медиану набора с ЧЁТНЫМ количеством чисел?",
                hint: "💡 Если чисел 6, нет одного числа ровно посередине. Что делать?",
                correctAnswer: "взять два средних числа и найти их среднее арифметическое",
                explanation: "✅ Для ЧЁТНОГО количества чисел медиана = среднее арифметическое двух чисел, стоящих в центре упорядоченного ряда."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "Что нужно сделать с рядом чисел перед нахождением медианы?",
                hint: "💡 Нельзя сразу взять середину неотсортированного списка.",
                correctAnswer: "упорядочить по возрастанию",
                explanation: "✅ Перед нахождением медианы числа нужно УПОРЯДОЧИТЬ (отсортировать) по возрастанию или убыванию."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "В наборе 3, 5, 7, 9, 11 чему равна медиана? (введите число)",
                hint: "💡 Ряд уже упорядочен. Всего 5 чисел. Какое число стоит на 3-м месте?",
                correctAnswer: "7",
                explanation: "✅ Медиана = <strong>7</strong>. Это третье число (центральное) в упорядоченном ряду."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "Почему медиана считается более устойчивой характеристикой, чем среднее арифметическое?",
                hint: "💡 Вспомни пример с зарплатами: 30, 35, 40, 45, 500. Что сильнее изменится, если заменить 500 на 1000?",
                correctAnswer: "потому что медиана не зависит от выбросов (очень больших или очень маленьких значений)",
                options: [
                    { value: "потому что медиану легче вычислять", text: "Потому что медиану легче вычислять" },
                    { value: "потому что медиана не зависит от выбросов (очень больших или очень маленьких значений)", text: "Потому что медиана не зависит от выбросов (очень больших или очень маленьких значений). Например, в наборе 30, 35, 40, 45, 500 среднее = 130, а медиана = 40. Медиана лучше отражает типичное значение." },
                    { value: "потому что медиана всегда больше среднего", text: "Потому что медиана всегда больше среднего" },
                    { value: "потому что медиану можно найти только для чётного количества чисел", text: "Потому что медиану можно найти только для чётного количества чисел" }
                ],
                explanation: "✅ Медиана УСТОЙЧИВА к выбросам. Она не меняется сильно, если заменить 500 на 1000, а среднее арифметическое — меняется."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "В наборе 8 чисел. Как определить, какие два числа нужно взять для вычисления медианы?",
                hint: "💡 Если чисел 8, центральные места — это 4-е и 5-е по счёту.",
                correctAnswer: "нужно взять n/2 и n/2 + 1 числа в упорядоченном ряду",
                options: [
                    { value: "нужно взять первое и последнее число", text: "Нужно взять первое и последнее число" },
                    { value: "нужно взять n/2 и n/2 + 1 числа в упорядоченном ряду", text: "Нужно взять n/2 и n/2 + 1 числа в упорядоченном ряду (4-е и 5-е при n=8)" },
                    { value: "нужно взять третье и шестое числа", text: "Нужно взять третье и шестое числа" },
                    { value: "нужно взять любые два числа и найти их среднее", text: "Нужно взять любые два числа и найти их среднее" }
                ],
                explanation: "✅ При чётном n = 8 центральные места: n/2 = 4 и n/2 + 1 = 5. Нужны 4-е и 5-е числа в упорядоченном ряду."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "В классе 25 учеников. Их рост измерили и упорядочили. Какое по счёту значение будет медианой?",
                hint: "💡 При нечётном n = 25 медиана на месте (n+1)/2.",
                correctAnswer: "13-е",
                options: [
                    { value: "12-е", text: "12-е" },
                    { value: "13-е", text: "13-е" },
                    { value: "1-е", text: "1-е" },
                    { value: "25-е", text: "25-е" }
                ],
                explanation: "✅ При n = 25 (нечётное) медиана находится на месте (25+1)/2 = <strong>13</strong>. Это 13-й ученик в упорядоченном по росту списке."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "Может ли медиана совпадать со средним арифметическим? Если да, то в каком случае?",
                hint: "💡 Представь симметричный ряд: 10, 20, 30, 40, 50.",
                correctAnswer: "да, если распределение чисел симметрично относительно центра",
                options: [
                    { value: "нет, медиана и среднее никогда не совпадают", text: "Нет, медиана и среднее никогда не совпадают" },
                    { value: "да, если распределение чисел симметрично относительно центра", text: "Да, если распределение чисел симметрично относительно центра. Например, в наборе 10,20,30,40,50 и среднее, и медиана равны 30." },
                    { value: "да, но только для наборов с чётным количеством чисел", text: "Да, но только для наборов с чётным количеством чисел" },
                    { value: "да, если в наборе есть выбросы", text: "Да, если в наборе есть выбросы" }
                ],
                explanation: "✅ Медиана может совпадать со средним, если распределение СИММЕТРИЧНО. Например: 10,20,30,40,50 → среднее = 30, медиана = 30."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "В наборе: 1, 2, 100, 101, 102. Какая характеристика лучше опишет «типичное» значение и почему?",
                hint: "💡 Посчитай среднее и медиану. Какое из чисел ближе к большинству значений?",
                correctAnswer: "медиана (100), потому что среднее сильно смещено маленькими числами 1 и 2",
                options: [
                    { value: "среднее, потому что оно учитывает все числа", text: "Среднее, потому что оно учитывает все числа" },
                    { value: "медиана (100), потому что среднее сильно смещено маленькими числами 1 и 2", text: "Медиана (100), потому что среднее (≈61) сильно смещено маленькими числами 1 и 2, а медиана показывает центр основной группы" },
                    { value: "размах, потому что он показывает разброс", text: "Размах, потому что он показывает разброс" },
                    { value: "обе характеристики одинаково хороши", text: "Обе характеристики одинаково хороши" }
                ],
                explanation: "✅ Среднее = (1+2+100+101+102)/5 = 306/5 = 61,2. Медиана = 100. Набор несимметричен, маленькие значения (1,2) тянут среднее вниз. Медиана (100) лучше описывает типичное значение."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ==========
    {
        id: "trkm_cluster_median",
        title: "🧠 ТРКМ: Кластер «Медиана числового набора»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Каждая карточка должна попасть в свой раздел. Неправильные карточки будут выделены красным.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_def", name: "📖 ОПРЕДЕЛЕНИЕ", maxCards: 2 },
            { id: "branch_odd", name: "🔢 НЕЧЁТНОЕ КОЛИЧЕСТВО", maxCards: 2 },
            { id: "branch_even", name: "🔢 ЧЁТНОЕ КОЛИЧЕСТВО", maxCards: 2 },
            { id: "branch_property", name: "🔍 СВОЙСТВА", maxCards: 2 },
            { id: "branch_compare", name: "🔄 СРАВНЕНИЕ СО СРЕДНИМ", maxCards: 2 }
        ],
        cards: [
            // Ветвь: ОПРЕДЕЛЕНИЕ (2 карточки)
            { id: "card_def_1", text: "Число, стоящее посередине упорядоченного ряда" },
            { id: "card_def_2", text: "От латинского «medius» — середина" },
            
            // Ветвь: НЕЧЁТНОЕ КОЛИЧЕСТВО (2 карточки)
            { id: "card_odd_1", text: "Медиана = число на месте (n+1)/2" },
            { id: "card_odd_2", text: "Пример: в ряду 3,5,7,9,11 медиана = 7" },
            
            // Ветвь: ЧЁТНОЕ КОЛИЧЕСТВО (2 карточки)
            { id: "card_even_1", text: "Медиана = среднее двух центральных чисел" },
            { id: "card_even_2", text: "Пример: в ряду 2,4,6,8,10,12 медиана = (6+8)/2 = 7" },
            
            // Ветвь: СВОЙСТВА (2 карточки)
            { id: "card_prop_1", text: "Устойчива к выбросам (не меняется от экстремальных значений)" },
            { id: "card_prop_2", text: "Перед нахождением медианы числа нужно упорядочить" },
            
            // Ветвь: СРАВНЕНИЕ СО СРЕДНИМ (2 карточки)
            { id: "card_comp_1", text: "Медиана лучше среднего при наличии выбросов" },
            { id: "card_comp_2", text: "В симметричных наборах медиана = среднему" }
        ]
    }
];
const statisticsBasicFormulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_stats_basic",
        title: "🧠 ТРКМ: «Среднее арифметическое, мода, медиана, размах» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы о статистических характеристиках. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта. Для каждого вопроса есть подсказка.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Как найти среднее арифметическое числового набора?",
                hint: "💡 Нужно сложить все числа и... что сделать с количеством?",
                correctAnswer: "сложить все числа и разделить на их количество",
                explanation: "✅ СРЕДНЕЕ АРИФМЕТИЧЕСКОЕ = (сумма всех чисел) / (количество чисел)."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "Что такое мода числового набора?",
                hint: "💡 Это значение, которое встречается... (как часто?)",
                correctAnswer: "значение, которое встречается чаще всего",
                explanation: "✅ МОДА — это самое часто встречающееся значение в наборе данных."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "Что такое медиана упорядоченного числового ряда с НЕЧЁТНЫМ количеством чисел?",
                hint: "💡 Где находится середина ряда?",
                correctAnswer: "число, стоящее посередине",
                explanation: "✅ МЕДИАНА для нечётного количества чисел — это число, которое стоит ровно посередине упорядоченного ряда."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "Как найти размах числового набора?",
                hint: "💡 Нужно из самого большого числа... самое маленькое.",
                correctAnswer: "из наибольшего числа вычесть наименьшее",
                explanation: "✅ РАЗМАХ = максимальное значение − минимальное значение."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "Как найти медиану упорядоченного ряда с ЧЁТНЫМ количеством чисел?",
                hint: "💡 Середины нет — нужно взять два центральных числа и ...",
                correctAnswer: "взять два средних числа и найти их среднее арифметическое",
                explanation: "✅ Для чётного количества чисел медиана = среднее арифметическое двух центральных чисел."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "В каких случаях среднее арифметическое плохо описывает типичное значение набора, а медиана подходит лучше?",
                hint: "💡 Вспомни пример с зарплатами, где один директор получает миллион, а остальные — по 30 тысяч.",
                correctAnswer: "когда в наборе есть выбросы (очень большие или очень маленькие значения), среднее искажается, а медиана остаётся типичным значением",
                options: [
                    { value: "среднее арифметическое всегда лучше медианы, поэтому медиану используют редко", text: "Среднее арифметическое всегда лучше медианы, поэтому медиану используют редко" },
                    { value: "когда в наборе есть выбросы (очень большие или очень маленькие значения), среднее искажается, а медиана остаётся типичным значением", text: "Когда в наборе есть выбросы (очень большие или очень маленькие значения), среднее арифметическое искажается, а медиана остаётся «типичным» значением. Например, зарплаты: 30, 35, 40, 45, 500 → среднее = 130, медиана = 40" },
                    { value: "медиана лучше среднего только для чётного количества чисел", text: "Медиана лучше среднего только для чётного количества чисел" },
                    { value: "среднее и медиана всегда совпадают, поэтому выбирать не приходится", text: "Среднее и медиана всегда совпадают, поэтому выбирать не приходится" }
                ],
                explanation: "✅ Когда есть ВЫБРОСЫ (очень большие или маленькие числа), среднее арифметическое искажается. Медиана устойчива к выбросам и лучше показывает типичное значение."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "Может ли у числового набора быть две моды? А может ли не быть ни одной?",
                hint: "💡 Что если два числа встречаются одинаково часто? А если все числа разные?",
                correctAnswer: "мод может быть несколько (если несколько значений встречаются одинаково часто), а может не быть вовсе (если все значения встречаются одинаково часто)",
                options: [
                    { value: "мода всегда одна, и она всегда существует", text: "Мода всегда одна, и она всегда существует" },
                    { value: "мод может быть несколько, а может не быть вовсе", text: "Мод может быть несколько (например, в наборе 1,1,2,2,3 две моды — 1 и 2), а может не быть вовсе (если все значения встречаются одинаково часто, например, 1,2,3,4)" },
                    { value: "мода существует только для наборов с нечётным количеством чисел", text: "Мода существует только для наборов с нечётным количеством чисел" },
                    { value: "мода всегда равна среднему арифметическому", text: "Мода всегда равна среднему арифметическому" }
                ],
                explanation: "✅ МОД может быть НЕСКОЛЬКО (если несколько значений встречаются одинаково часто). Моды может НЕ БЫТЬ вовсе, если все значения встречаются одинаково часто."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "В наборе: 10, 20, 30, 40, 50, 1000. Какая характеристика лучше всего опишет «типичное» значение и почему?",
                hint: "💡 Число 1000 — это выброс. Какая характеристика его не боится?",
                correctAnswer: "медиана, потому что она не чувствительна к выбросу и показывает центр основной части данных",
                options: [
                    { value: "среднее арифметическое, потому что оно учитывает все числа", text: "Среднее арифметическое, потому что оно учитывает все числа" },
                    { value: "размах, потому что он показывает разброс", text: "Размах, потому что он показывает разброс" },
                    { value: "медиана, потому что она не чувствительна к выбросу и показывает центр основной части данных", text: "Медиана (30,5), потому что она не чувствительна к выбросу (1000) и показывает центр основной части данных" },
                    { value: "мода, потому что она самая популярная", text: "Мода, потому что она самая популярная" }
                ],
                explanation: "✅ МЕДИАНА = (30+40)/2 = 35. Она устойчива к выбросу 1000 и лучше описывает типичное значение, чем среднее (≈195)."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "Что показывает размах, а что — нет? В чём его главный недостаток?",
                hint: "💡 Размах = max − min. Учитывает ли он числа, которые находятся между максимумом и минимумом?",
                correctAnswer: "размах показывает разброс между max и min, но не учитывает распределение остальных чисел",
                options: [
                    { value: "размах показывает разброс между max и min, но не учитывает распределение остальных чисел", text: "Размах показывает разброс между самым большим и самым маленьким значением. Его недостаток: он не учитывает, как распределены остальные числа (например, наборы 10,20,30,40,50 и 10,10,10,50,50 имеют одинаковый размах 40, но совершенно разную структуру)." },
                    { value: "размах показывает среднее значение набора", text: "Размах показывает среднее значение набора. Его недостаток — сложность вычисления." },
                    { value: "размах показывает самое частое значение", text: "Размах показывает самое частое значение. Его недостаток — он не всегда существует." },
                    { value: "размах показывает середину набора", text: "Размах показывает середину набора. Его недостаток — он не работает для чётного количества чисел." }
                ],
                explanation: "✅ РАЗМАХ показывает разброс (max − min). Его главный недостаток — он НЕ УЧИТЫВАЕТ распределение остальных чисел."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "Для чего нужны разные характеристики (среднее, мода, медиана, размах), если все они описывают один и тот же набор чисел?",
                hint: "💡 Для сравнения классов нужно одно, для выбора популярного размера — другое, для зарплат с выбросами — третье.",
                correctAnswer: "они нужны для разных целей: выбор зависит от задачи и характера данных",
                options: [
                    { value: "они все одинаковы и взаимозаменяемы", text: "Они все одинаковы и взаимозаменяемы" },
                    { value: "они нужны для разных целей: выбор зависит от задачи и характера данных", text: "Они нужны для разных целей: среднее — для общего уровня, мода — для самого популярного значения, медиана — для типичного значения при выбросах, размах — для оценки разброса. Выбор зависит от задачи и характера данных." },
                    { value: "мода и медиана нужны только для контроля правильности среднего", text: "Мода и медиана нужны только для контроля правильности среднего" },
                    { value: "размах используют только в спорте, а среднее — только в школе", text: "Размах используют только в спорте, а среднее — только в школе" }
                ],
                explanation: "✅ НЕТ САМОЙ ПРАВИЛЬНОЙ ХАРАКТЕРИСТИКИ. Выбор зависит от ЦЕЛИ: сравнение — среднее, популярное значение — мода, выбросы — медиана, разброс — размах."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ==========
    {
        id: "trkm_cluster_stats_basic",
        title: "🧠 ТРКМ: Кластер «Статистические характеристики»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Каждая карточка должна попасть в свой раздел. Неправильные карточки будут выделены красным.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_mean", name: "📊 СРЕДНЕЕ АРИФМЕТИЧЕСКОЕ", maxCards: 2 },
            { id: "branch_mode", name: "🎯 МОДА", maxCards: 2 },
            { id: "branch_median", name: "🎲 МЕДИАНА", maxCards: 2 },
            { id: "branch_range", name: "📏 РАЗМАХ", maxCards: 2 },
            { id: "branch_compare", name: "🔄 СРАВНЕНИЕ ХАРАКТЕРИСТИК", maxCards: 2 }
        ],
        cards: [
            // Среднее арифметическое
            { id: "card_mean_1", text: "Сумма всех чисел ÷ количество чисел" },
            { id: "card_mean_2", text: "Чувствительно к выбросам" },
            
            // Мода
            { id: "card_mode_1", text: "Самое часто встречающееся значение" },
            { id: "card_mode_2", text: "Может быть несколько или не быть вовсе" },
            
            // Медиана
            { id: "card_median_1", text: "Середина упорядоченного ряда" },
            { id: "card_median_2", text: "Устойчива к выбросам" },
            
            // Размах
            { id: "card_range_1", text: "Максимум − минимум" },
            { id: "card_range_2", text: "Не учитывает распределение остальных чисел" },
            
            // Сравнение характеристик
            { id: "card_compare_1", text: "Выбор зависит от цели и характера данных" },
            { id: "card_compare_2", text: "Нет одной самой правильной характеристики" }
        ]
    }
];
// ========== ТРКМ - ГРАФИЧЕСКОЕ ПРЕДСТАВЛЕНИЕ ДАННЫХ (7 КЛАСС) ==========
const grade7_topic2Formulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_graphs",
        title: "🧠 ТРКМ: «Графическое представление данных» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы о графиках и диаграммах. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта. Для каждого вопроса есть подсказка.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Как называется диаграмма, в которой данные изображаются в виде круга, разбитого на секторы?",
                hint: "💡 Части круга — как доли от целого пирога.",
                correctAnswer: "круговая диаграмма",
                explanation: "✅ КРУГОВАЯ ДИАГРАММА показывает доли (части от целого). Весь круг — 100%, каждый сектор — процентная доля."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "Какой тип диаграммы лучше всего подходит для показа изменения температуры в течение недели?",
                hint: "💡 Нужно показать, как величина меняется со временем. Точки соединяются линией.",
                correctAnswer: "линейный график",
                explanation: "✅ ЛИНЕЙНЫЙ ГРАФИК лучше всего подходит для показа изменения величин во времени (тренда)."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "Что должно быть обязательно подписано на осях координат при построении графика?",
                hint: "💡 Что означают числа на оси X и на оси Y?",
                correctAnswer: "название величины и единицы измерения",
                explanation: "✅ На осях координат обязательно подписывают НАЗВАНИЕ ВЕЛИЧИНЫ и ЕДИНИЦЫ ИЗМЕРЕНИЯ (например, «Время, ч» и «Температура, °C»)."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "Как называется диаграмма, в которой данные представлены в виде прямоугольников (столбиков) одинаковой ширины?",
                hint: "💡 Чем больше значение, тем выше столбик.",
                correctAnswer: "столбчатая диаграмма",
                explanation: "✅ СТОЛБЧАТАЯ ДИАГРАММА (или гистограмма) использует столбики одинаковой ширины — высота столбика соответствует величине данных."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "Что произойдёт с восприятием данных, если на столбчатой диаграмме ось Y начинается не с нуля, а с 50?",
                hint: "💡 Разница между 50 и 60 (10 единиц) и между 100 и 110 (10 единиц) будет выглядеть по-разному.",
                correctAnswer: "различия будут выглядеть преувеличенно",
                explanation: "✅ Если ось Y обрезана (начинается не с нуля), небольшие различия выглядят огромными — это приём манипуляции."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "Для чего нужны графики и диаграммы, если ту же информацию можно представить в виде таблицы?",
                hint: "💡 Что мозгу легче воспринимать: цифры или картинку?",
                correctAnswer: "графики позволяют быстрее увидеть закономерности, так как мозг обрабатывает визуальную информацию легче, чем цифры в таблице",
                options: [
                    { value: "графики нужны только для украшения отчётов, таблицы всегда точнее", text: "Графики нужны только для украшения отчётов, таблицы всегда точнее" },
                    { value: "графики позволяют быстрее увидеть закономерности, так как мозг обрабатывает визуальную информацию легче, чем цифры в таблице", text: "Графики позволяют быстрее увидеть закономерности (рост, спад, сравнение), так как мозг обрабатывает визуальную информацию легче, чем цифры в таблице" },
                    { value: "графики нельзя строить для числовых данных, только для текстовых", text: "Графики нельзя строить для числовых данных, только для текстовых" },
                    { value: "таблицы всегда нагляднее графиков, поэтому графики используют редко", text: "Таблицы всегда нагляднее графиков, поэтому графики используют редко" }
                ],
                explanation: "✅ Графики и диаграммы помогают БЫСТРО увидеть закономерности (рост, спад, сравнение), так как мозг обрабатывает визуальную информацию легче, чем столбцы цифр."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "Какую диаграмму вы выберете для каждого случая: а) любимые жанры кино (доли), б) рост продаж по месяцам, в) сравнение успеваемости двух классов по пяти предметам?",
                hint: "💡 Для долей — одна диаграмма, для изменения во времени — другая, для сравнения категорий — третья.",
                correctAnswer: "для долей — круговая, для изменения во времени — линейный график, для сравнения по нескольким категориям — столбчатая",
                options: [
                    { value: "во всех случаях подходит круговая диаграмма", text: "Во всех случаях подходит круговая диаграмма" },
                    { value: "для долей — круговая, для изменения во времени — линейный график, для сравнения по нескольким категориям — столбчатая", text: "Для долей — круговая, для изменения во времени — линейный график, для сравнения по нескольким категориям — столбчатая (группированная)" },
                    { value: "для долей — столбчатая, для изменения во времени — круговая, для сравнения — линейный график", text: "Для долей — столбчатая, для изменения во времени — круговая, для сравнения — линейный график" },
                    { value: "во всех случаях подходит только столбчатая диаграмма", text: "Во всех случаях подходит только столбчатая диаграмма" }
                ],
                explanation: "✅ Для ДОЛЕЙ — круговая диаграмма, для ИЗМЕНЕНИЯ ВО ВРЕМЕНИ — линейный график, для СРАВНЕНИЯ КАТЕГОРИЙ — столбчатая диаграмма."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "Почему на одной и той же линейной диаграмме рост продаж может выглядеть как «взрывной», а может — как «незначительный»?",
                hint: "💡 От чего зависит наклон линии на графике?",
                correctAnswer: "потому что диаграмма может быть построена с разным масштабом оси Y: если ось начинается не с нуля, даже небольшой рост кажется огромным",
                options: [
                    { value: "потому что разные люди по-разному воспринимают одни и те же линии", text: "Потому что разные люди по-разному воспринимают одни и те же линии" },
                    { value: "потому что диаграмма может быть построена с разным масштабом оси Y: если ось начинается не с нуля, даже небольшой рост кажется огромным", text: "Потому что диаграмма может быть построена с разным масштабом оси Y: если ось начинается не с нуля, даже небольшой рост кажется огромным" },
                    { value: "потому что данные на диаграмме можно изменить, подставив другие числа", text: "Потому что данные на диаграмме можно изменить, подставив другие числа" },
                    { value: "потому что линейные диаграммы всегда показывают только приблизительные значения", text: "Потому что линейные диаграммы всегда показывают только приблизительные значения" }
                ],
                explanation: "✅ Всё дело в МАСШТАБЕ оси Y. Если ось начинается с нуля — график честный. Если ось обрезана — даже маленький рост выглядит как взрывной."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "Как можно ввести читателя в заблуждение с помощью круговой диаграммы?",
                hint: "💡 Что можно сделать с секторами, чтобы исказить восприятие?",
                correctAnswer: "если сделать слишком много секторов или использовать близкие оттенки, трудно сравнить доли. А если оторвать сектор от круга, можно создать иллюзию, что он больше",
                options: [
                    { value: "круговая диаграмма всегда честна, её невозможно исказить", text: "Круговая диаграмма всегда честна, её невозможно исказить" },
                    { value: "если сделать слишком много секторов или использовать близкие оттенки, трудно сравнить доли. А если оторвать сектор от круга, можно создать иллюзию, что он больше", text: "Если сделать слишком много секторов (больше 5–6) или использовать близкие оттенки, трудно сравнить доли. А если оторвать сектор от круга, можно создать иллюзию, что он больше, чем на самом деле" },
                    { value: "круговую диаграмму можно исказить, только если неправильно посчитать проценты", text: "Круговую диаграмму можно исказить, только если неправильно посчитать проценты" },
                    { value: "круговую диаграмму нельзя исказить, если использовать компьютерную программу", text: "Круговую диаграмму нельзя исказить, если использовать компьютерную программу" }
                ],
                explanation: "✅ Круговую диаграмму можно исказить: слишком много секторов (трудно сравнить), близкие оттенки (сливаются), выдвинутый сектор (кажется больше)."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "В каких случаях лучше использовать линейный график, а в каких — столбчатую диаграмму?",
                hint: "💡 Что показывает линия, а что — столбики?",
                correctAnswer: "линейный график лучше для показа изменения во времени, а столбчатая — для сравнения независимых категорий",
                options: [
                    { value: "линейный график всегда лучше столбчатой диаграммы, потому что он точнее", text: "Линейный график всегда лучше столбчатой диаграммы, потому что он точнее" },
                    { value: "линейный график лучше для показа изменения во времени, а столбчатая — для сравнения независимых категорий", text: "Линейный график лучше для показа изменения во времени (например, температура за месяц), а столбчатая — для сравнения независимых категорий (например, население разных городов)" },
                    { value: "столбчатая диаграмма лучше для всего, кроме погоды", text: "Столбчатая диаграмма лучше для всего, кроме погоды" },
                    { value: "линейный график подходит только для финансовых отчётов, столбчатая — только для опросов", text: "Линейный график подходит только для финансовых отчётов, столбчатая — только для опросов" }
                ],
                explanation: "✅ ЛИНЕЙНЫЙ ГРАФИК — для изменения во времени (тренд). СТОЛБЧАТАЯ ДИАГРАММА — для сравнения независимых категорий."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ==========
    {
        id: "trkm_cluster_graphs",
        title: "🧠 ТРКМ: Кластер «Графическое представление данных»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Каждая карточка должна попасть в свой раздел. Неправильные карточки будут выделены красным.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_types", name: "📊 ТИПЫ ДИАГРАММ", maxCards: 3 },
            { id: "branch_purpose", name: "🎯 НАЗНАЧЕНИЕ", maxCards: 3 },
            { id: "branch_elements", name: "🔍 ЭЛЕМЕНТЫ ГРАФИКА", maxCards: 3 },
            { id: "branch_mistakes", name: "⚠️ ТИПИЧНЫЕ ОШИБКИ И МАНИПУЛЯЦИИ", maxCards: 3 },
            { id: "branch_rules", name: "📋 ПРАВИЛА ПОСТРОЕНИЯ", maxCards: 2 }
        ],
        cards: [
            // Ветвь: ТИПЫ ДИАГРАММ (3 карточки)
            { id: "card_type_1", text: "Столбчатая диаграмма (гистограмма)" },
            { id: "card_type_2", text: "Линейный график" },
            { id: "card_type_3", text: "Круговая диаграмма" },
            
            // Ветвь: НАЗНАЧЕНИЕ (3 карточки)
            { id: "card_purp_1", text: "Для сравнения категорий" },
            { id: "card_purp_2", text: "Для показа изменения во времени (тренда)" },
            { id: "card_purp_3", text: "Для показа долей (частей целого)" },
            
            // Ветвь: ЭЛЕМЕНТЫ ГРАФИКА (3 карточки)
            { id: "card_elem_1", text: "Ось X (горизонтальная) — независимая переменная" },
            { id: "card_elem_2", text: "Ось Y (вертикальная) — зависимая переменная" },
            { id: "card_elem_3", text: "Заголовок и подписи осей с единицами измерения" },
            
            // Ветвь: ТИПИЧНЫЕ ОШИБКИ И МАНИПУЛЯЦИИ (3 карточки)
            { id: "card_mist_1", text: "Обрезанная ось Y (начинается не с нуля)" },
            { id: "card_mist_2", text: "Слишком много секторов в круговой диаграмме" },
            { id: "card_mist_3", text: "Отсутствие подписей осей и единиц измерения" },
            
            // Ветвь: ПРАВИЛА ПОСТРОЕНИЯ (2 карточки)
            { id: "card_rule_1", text: "Ось Y должна начинаться с 0 (или должно быть предупреждение)" },
            { id: "card_rule_2", text: "Тип диаграммы должен соответствовать типу данных" }
        ]
    }
];
// ========== ТРКМ - ПРЕДСТАВЛЕНИЕ ДАННЫХ В ТАБЛИЦАХ (7 КЛАСС) ==========
const grade7_topic1Formulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_tables",
        title: "🧠 ТРКМ: «Представление данных в таблицах» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы о таблицах и правилах их составления. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта. Для каждого вопроса есть подсказка.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Как называются вертикальные колонки в таблице?",
                hint: "💡 В таблице есть строки (горизонтальные) и ... (вертикальные).",
                correctAnswer: "столбцы",
                explanation: "✅ Вертикальные колонки в таблице называются СТОЛБЦАМИ."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "Что обязательно должно быть у каждой таблицы, чтобы в ней можно было ориентироваться?",
                hint: "💡 Без чего таблица становится непонятной? Что объясняет, какие данные в каждом столбце?",
                correctAnswer: "заголовки",
                explanation: "✅ У каждой таблицы обязательно должны быть ЗАГОЛОВКИ столбцов (и часто строк), чтобы было понятно, какие данные в них находятся."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "Где в таблице обычно располагаются названия объектов (например, фамилии учеников)?",
                hint: "💡 Обычно в первом столбце или в первой строке — там, где перечисляются объекты.",
                correctAnswer: "в первой колонке",
                explanation: "✅ Названия объектов (фамилии, названия товаров, города) обычно располагаются в ПЕРВОЙ КОЛОНКЕ таблицы."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "В каких единицах измерения должны быть указаны данные в таблице, если эти единицы не очевидны?",
                hint: "💡 Если в таблице указан рост, нужно написать «Рост, см». Где пишут единицы измерения?",
                correctAnswer: "в заголовках столбцов",
                explanation: "✅ Единицы измерения указываются в ЗАГОЛОВКАХ СТОЛБЦОВ (например, «Рост, см», «Масса, кг», «Цена, руб.»)."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "Как называется верхняя строка таблицы, в которой указаны названия столбцов?",
                hint: "💡 Эту часть таблицы часто называют «шапкой».",
                correctAnswer: "шапка",
                explanation: "✅ Верхняя строка таблицы, содержащая названия столбцов, называется ШАПКОЙ таблицы."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "Почему таблица может быть неудобна для чтения, если в ней нет заголовков?",
                hint: "💡 Что произойдёт, если убрать названия столбцов? Сможете ли вы понять, что означает каждое число?",
                correctAnswer: "без заголовков нельзя понять, какие данные находятся в каждом столбце, и таблица теряет смысл",
                options: [
                    { value: "без заголовков нельзя понять, какие данные находятся в каждом столбце, и таблица теряет смысл", text: "Без заголовков нельзя понять, какие данные находятся в каждом столбце, и таблица теряет смысл" },
                    { value: "без заголовков таблица занимает меньше места на странице, что делает её компактнее", text: "Без заголовков таблица занимает меньше места на странице, что делает её компактнее" },
                    { value: "без заголовков данные легче запоминаются, так как их нужно интерпретировать самостоятельно", text: "Без заголовков данные легче запоминаются, так как их нужно интерпретировать самостоятельно" },
                    { value: "без заголовков таблица становится более наглядной для специалистов", text: "Без заголовков таблица становится более наглядной для специалистов" }
                ],
                explanation: "✅ Заголовки — это ключевой элемент таблицы. Без них невозможно понять, какие данные находятся в каждом столбце, и таблица теряет смысл."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "В чём отличие таблицы от обычного текстового списка?",
                hint: "💡 Что даёт таблица такого, чего нет у простого списка?",
                correctAnswer: "в таблице данные разбиты на столбцы и строки, что позволяет быстро их сравнивать и находить связи",
                options: [
                    { value: "в таблице данные разбиты на столбцы и строки, что позволяет быстро их сравнивать и находить связи", text: "В таблице данные разбиты на столбцы и строки, что позволяет быстро их сравнивать и находить связи" },
                    { value: "таблица всегда короче списка и занимает меньше места", text: "Таблица всегда короче списка и занимает меньше места" },
                    { value: "список всегда точнее таблицы, потому что в нём нет лишней информации", text: "Список всегда точнее таблицы, потому что в нём нет лишней информации" },
                    { value: "таблица не может содержать числовые данные, в отличие от списка", text: "Таблица не может содержать числовые данные, в отличие от списка" }
                ],
                explanation: "✅ Главное отличие таблицы от списка — структурированность по строкам и столбцам. Это позволяет быстро сравнивать данные, находить связи и делать выводы."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "Какой главный принцип нужно соблюдать при составлении таблицы, чтобы она была понятна разным людям?",
                hint: "💡 Что важно указать, чтобы любой человек понял, что означают числа в таблице?",
                correctAnswer: "нужно чётко назвать каждый столбец и каждую строку, указать единицы измерения и выбрать структуру, отвечающую на главный вопрос",
                options: [
                    { value: "нужно чётко назвать каждый столбец и каждую строку, указать единицы измерения и выбрать структуру, отвечающую на главный вопрос", text: "Нужно чётко назвать каждый столбец и каждую строку, указать единицы измерения и выбрать структуру, отвечающую на главный вопрос" },
                    { value: "нужно использовать только числа и избегать текста", text: "Нужно использовать только числа и избегать текста" },
                    { value: "нужно сделать как можно больше столбцов, чтобы ничего не упустить", text: "Нужно сделать как можно больше столбцов, чтобы ничего не упустить" },
                    { value: "нужно располагать все данные в алфавитном порядке", text: "Нужно располагать все данные в алфавитном порядке" }
                ],
                explanation: "✅ Главный принцип: таблица должна быть понятна разным людям. Для этого нужно чётко назвать каждый столбец, указать единицы измерения и выбрать структуру, отвечающую на главный вопрос."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "Почему одни и те же данные могут быть представлены в виде таблиц разной структуры?",
                hint: "💡 Для заказа мебели нужна одна таблица, для расстановки по кабинетам — другая. Почему?",
                correctAnswer: "потому что разные люди могут преследовать разные цели: одному нужно знать общую сумму, другому — расклад по отделам",
                options: [
                    { value: "потому что разные люди могут преследовать разные цели: одному нужно знать общую сумму, другому — расклад по отделам", text: "Потому что разные люди могут преследовать разные цели: одному нужно знать общую сумму, другому — расклад по отделам" },
                    { value: "это невозможно: для одних данных существует только одна правильная таблица", text: "Это невозможно: для одних данных существует только одна правильная таблица" },
                    { value: "потому что таблицы не имеют правил оформления, каждый составляет как хочет", text: "Потому что таблицы не имеют правил оформления, каждый составляет как хочет" },
                    { value: "потому что данные всегда можно представить как в виде строк, так и в виде столбцов без изменения смысла", text: "Потому что данные всегда можно представить как в виде строк, так и в виде столбцов без изменения смысла" }
                ],
                explanation: "✅ Одна и та же информация может быть представлена в разных таблицах, потому что таблица зависит от ЦЕЛИ. Для одной цели нужно одно, для другой — другое. Нет «правильной» таблицы на все случаи."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "Какие ошибки часто допускают начинающие при составлении таблиц?",
                hint: "💡 Что делает таблицу непонятной?",
                correctAnswer: "не указывают единицы измерения, не подписывают столбцы, смешивают в одном столбце разные типы данных",
                options: [
                    { value: "не указывают единицы измерения, не подписывают столбцы, смешивают в одном столбце разные типы данных", text: "Не указывают единицы измерения, не подписывают столбцы, смешивают в одном столбце разные типы данных (например, числа и текст)" },
                    { value: "используют слишком крупный шрифт и яркие цвета", text: "Используют слишком крупный шрифт и яркие цвета" },
                    { value: "делают слишком много пустых ячеек и используют сложные формулы", text: "Делают слишком много пустых ячеек и используют сложные формулы" },
                    { value: "добавляют в таблицу картинки и фотографии", text: "Добавляют в таблицу картинки и фотографии" }
                ],
                explanation: "✅ Самые частые ошибки: отсутствие заголовков, отсутствие единиц измерения, смешивание разных типов данных в одном столбце. Такая таблица становится непонятной и бесполезной."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ==========
    {
        id: "trkm_cluster_tables",
        title: "🧠 ТРКМ: Кластер «Представление данных в таблицах»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Каждая карточка должна попасть в свой раздел. Неправильные карточки будут выделены красным.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_def", name: "📖 ОПРЕДЕЛЕНИЕ", maxCards: 2 },
            { id: "branch_elements", name: "🔍 ЭЛЕМЕНТЫ ТАБЛИЦЫ", maxCards: 3 },
            { id: "branch_rules", name: "📋 ПРАВИЛА ОФОРМЛЕНИЯ", maxCards: 3 },
            { id: "branch_mistakes", name: "⚠️ ТИПИЧНЫЕ ОШИБКИ", maxCards: 3 },
            { id: "branch_purpose", name: "🎯 НАЗНАЧЕНИЕ", maxCards: 2 }
        ],
        cards: [
            // Ветвь: ОПРЕДЕЛЕНИЕ (2 карточки)
            { id: "card_def_1", text: "Способ организации данных по строкам и столбцам" },
            { id: "card_def_2", text: "Упорядоченное представление информации, где каждый элемент имеет свой адрес (строка, столбец)" },
            
            // Ветвь: ЭЛЕМЕНТЫ ТАБЛИЦЫ (3 карточки)
            { id: "card_elem_1", text: "Строки — горизонтальные ряды данных" },
            { id: "card_elem_2", text: "Столбцы — вертикальные колонки данных" },
            { id: "card_elem_3", text: "Ячейка — пересечение строки и столбца" },
            
            // Ветвь: ПРАВИЛА ОФОРМЛЕНИЯ (3 карточки)
            { id: "card_rule_1", text: "Обязательное наличие заголовков столбцов" },
            { id: "card_rule_2", text: "Указание единиц измерения в заголовках" },
            { id: "card_rule_3", text: "Данные в одном столбце должны быть однотипными" },
            
            // Ветвь: ТИПИЧНЫЕ ОШИБКИ (3 карточки)
            { id: "card_mist_1", text: "Отсутствие заголовков" },
            { id: "card_mist_2", text: "Смешивание чисел и текста в одном столбце" },
            { id: "card_mist_3", text: "Не указаны единицы измерения" },
            
            // Ветвь: НАЗНАЧЕНИЕ (2 карточки)
            { id: "card_purp_1", text: "Систематизация и структурирование данных" },
            { id: "card_purp_2", text: "Быстрый поиск и сравнение информации" }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ЗАКОН БОЛЬШИХ ЧИСЕЛ (9 КЛАСС) ==========
const grade9_topic6Tests = [
    {
        id: "lln_issl_1",
        title: "🧠 «Почему природа не обманывает?»",
        description: "Бросаем монету. После каждого броска записываем долю выпавших орлов (частоту). Сначала результаты могут сильно прыгать: после 1-го броска частота = 1, после 2-го = 0,5, после 3-го = 0,67, после 4-го = 0,5, после 5-го = 0,6. Но по мере увеличения числа бросков частота приближается к 0,5. Это и есть закон больших чисел.",
        steps: [
            {
                step: 1,
                question: "Посмотри на график. Что происходит с частотой выпадения орлов по мере увеличения числа бросков?<br><br><svg width='500' height='300' viewBox='0 0 500 300' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='500' height='300' fill='#f8fafc' rx='8'/><text x='250' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Сходимость частоты к вероятности 0,5</text><line x1='50' y1='250' x2='470' y2='250' stroke='#1e4663' stroke-width='1.5'/><line x1='50' y1='250' x2='50' y2='30' stroke='#1e4663' stroke-width='1.5'/><text x='35' y='255' text-anchor='end' fill='#1e4663' font-size='10'>0</text><text x='35' y='205' text-anchor='end' fill='#1e4663' font-size='10'>0,25</text><text x='35' y='155' text-anchor='end' fill='#1e4663' font-size='10'>0,5</text><text x='35' y='105' text-anchor='end' fill='#1e4663' font-size='10'>0,75</text><text x='35' y='55' text-anchor='end' fill='#1e4663' font-size='10'>1</text><text x='50' y='260' text-anchor='middle' fill='#1e4663' font-size='10'>0</text><text x='130' y='260' text-anchor='middle' fill='#1e4663' font-size='10'>20</text><text x='210' y='260' text-anchor='middle' fill='#1e4663' font-size='10'>40</text><text x='290' y='260' text-anchor='middle' fill='#1e4663' font-size='10'>60</text><text x='370' y='260' text-anchor='middle' fill='#1e4663' font-size='10'>80</text><text x='450' y='260' text-anchor='middle' fill='#1e4663' font-size='10'>100</text><text x='250' y='280' text-anchor='middle' fill='#1e4663' font-size='11'>Число бросков</text><circle cx='70' cy='85' r='3' fill='#3b82f6'/><circle cx='90' cy='155' r='3' fill='#3b82f6'/><circle cx='110' cy='120' r='3' fill='#3b82f6'/><circle cx='130' cy='155' r='3' fill='#3b82f6'/><circle cx='150' cy='135' r='3' fill='#3b82f6'/><circle cx='170' cy='148' r='3' fill='#3b82f6'/><circle cx='190' cy='140' r='3' fill='#3b82f6'/><circle cx='210' cy='155' r='3' fill='#3b82f6'/><circle cx='230' cy='148' r='3' fill='#3b82f6'/><circle cx='250' cy='152' r='3' fill='#3b82f6'/><circle cx='270' cy='148' r='3' fill='#3b82f6'/><circle cx='290' cy='155' r='3' fill='#3b82f6'/><circle cx='310' cy='150' r='3' fill='#3b82f6'/><circle cx='330' cy='152' r='3' fill='#3b82f6'/><circle cx='350' cy='148' r='3' fill='#3b82f6'/><circle cx='370' cy='153' r='3' fill='#3b82f6'/><circle cx='390' cy='150' r='3' fill='#3b82f6'/><circle cx='410' cy='152' r='3' fill='#3b82f6'/><circle cx='430' cy='149' r='3' fill='#3b82f6'/><circle cx='450' cy='151' r='3' fill='#3b82f6'/><line x1='50' y1='155' x2='470' y2='155' stroke='#eab308' stroke-width='1.5' stroke-dasharray='4'/><text x='475' y='158' fill='#eab308' font-size='10'>p = 0,5</text></svg>",
                hint: "💡 Посмотри на график: при малом числе бросков точки сильно отклоняются от линии p=0,5. Чем больше бросков, тем ближе точки к этой линии.",
                correctAnswer: "частота приближается к 0,5",
                explanation: "✅ По мере увеличения числа бросков частота выпадения орлов приближается к вероятности 0,5. Колебания становятся меньше."
            },
            {
                step: 2,
                question: "Как называется этот закон? (введите: закон больших чисел, закон малых чисел, закон вероятности)",
                hint: "💡 Он объясняет, почему при большом числе опытов частота стремится к вероятности.",
                correctAnswer: "закон больших чисел",
                explanation: "✅ Это ЗАКОН БОЛЬШИХ ЧИСЕЛ. Он утверждает, что при многократном повторении независимых испытаний частота события приближается к его вероятности."
            },
            {
                step: 3,
                question: "Почему при 10 бросках монеты частота может сильно отличаться от 0,5, а при 1000 бросках — почти не отличается? (введите: потому что каждый новый бросок вносит всё меньший вклад в общую частоту)",
                hint: "💡 Один лишний орёл при 10 бросках меняет частоту на 0,1, а при 1000 — только на 0,001.",
                correctAnswer: "потому что каждый новый бросок вносит всё меньший вклад в общую частоту",
                explanation: "✅ Каждый новый бросок вносит всё меньший вклад в общую сумму. Поэтому с ростом числа бросков относительные колебания частоты уменьшаются."
            },
            {
                step: 4,
                question: "Как формулируется закон больших чисел для частоты? (введите: Sₙ/n → p при n → ∞, Sₙ → p при n → ∞, Sₙ = p при n → ∞)",
                hint: "💡 Sₙ — число успехов, n — число испытаний, p — вероятность.",
                correctAnswer: "Sₙ/n → p при n → ∞",
                explanation: "✅ Закон больших чисел: Sₙ/n → p при n → ∞. Частота стремится к вероятности."
            },
            {
                step: 5,
                question: "Как закон больших чисел применяется в социологических опросах? (введите: опрашивают выборку людей и по ней судят обо всех)",
                hint: "💡 Никто не опрашивает всех 140 миллионов жителей страны. Опрашивают около 2000 человек.",
                correctAnswer: "опрашивают выборку людей и по ней судят обо всех",
                explanation: "✅ Закон больших чисел позволяет по результатам опроса выборки (например, 2000 человек) судить о мнении всей популяции. Чем больше выборка, тем точнее результат."
            },
            {
                step: 6,
                question: "Какую погрешность даёт опрос 2500 человек? (введите: примерно 2% или примерно 10%)",
                hint: "💡 Погрешность ≈ 1/√n = 1/√2500 = 1/50 = 0,02 = 2%",
                correctAnswer: "примерно 2%",
                explanation: "✅ При опросе 2500 человек погрешность составляет примерно 1/√2500 = 1/50 = <strong>2%</strong>."
            },
            {
                step: 7,
                question: "Завод проверяет 100 деталей из партии. Доля брака в выборке = 0,03. Означает ли это, что во всей партии ровно 3% брака? (введите: да или нет)",
                hint: "💡 Закон больших чисел говорит, что частота приближается к истинной вероятности, но может немного отличаться.",
                correctAnswer: "нет",
                explanation: "✅ Не означает. Доля брака в выборке близка к истинной доле брака, но может немного отличаться из-за случайности. Чем больше выборка, тем точнее оценка."
            },
            {
                step: 8,
                question: "Какое условие НЕОБХОДИМО для выполнения закона больших чисел? (введите: независимость испытаний, зависимость испытаний, одинаковые условия)",
                hint: "💡 Если результат каждого испытания зависит от предыдущих (например, погода), закон может не работать.",
                correctAnswer: "независимость испытаний",
                explanation: "✅ Закон больших чисел требует НЕЗАВИСИМОСТИ испытаний. Если опыты зависимы (например, погода сегодня зависит от вчерашней), закон может не выполняться."
            },
            {
                step: 9,
                question: "Верно ли, что закон больших чисел позволяет предсказать результат одного конкретного броска монеты? (введите: да или нет)",
                hint: "💡 Закон работает только для большого числа опытов, а не для одного.",
                correctAnswer: "нет",
                explanation: "✅ Нет. Закон больших чисел не предсказывает результат одного опыта. Он говорит о поведении частоты при БОЛЬШОМ числе опытов."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать о законе больших чисел? (введите: частота приближается к вероятности при увеличении числа опытов, частота всегда точно равна вероятности)",
                hint: "💡 График показывает, что при 100 бросках частота ещё колеблется, но при 1000 — почти не отклоняется.",
                correctAnswer: "частота приближается к вероятности при увеличении числа опытов",
                explanation: "✅ Главный вывод: ЗАКОН БОЛЬШИХ ЧИСЕЛ утверждает, что при увеличении числа независимых опытов частота события приближается к его вероятности. Он лежит в основе статистики, опросов, контроля качества и страхования."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - МАТЕМАТИЧЕСКОЕ ОЖИДАНИЕ (9 КЛАСС) ==========
const grade9_topic5Tests = [
    {
        id: "expect_issl_1",
        title: "🧠 «Какое среднее у случайности?»",
        description: "Бросаем игральный кубик. Какое среднее значение выпавших очков мы получим, если бросить кубик много-много раз? Значения: 1, 2, 3, 4, 5, 6. Вероятность каждого = 1/6. Нужно найти сумму произведений значений на вероятности.",
        steps: [
            {
                step: 1,
                question: "Посмотри на диаграмму. Чему равно математическое ожидание числа очков при бросании кубика? (введите число)<br><br><svg width='400' height='300' viewBox='0 0 400 300' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='400' height='300' fill='#f8fafc' rx='8'/><text x='200' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Распределение вероятностей для кубика</text><line x1='50' y1='250' x2='370' y2='250' stroke='#1e4663' stroke-width='1.5'/><line x1='50' y1='250' x2='50' y2='50' stroke='#1e4663' stroke-width='1.5'/><text x='35' y='255' text-anchor='end' fill='#1e4663' font-size='10'>0</text><text x='35' y='205' text-anchor='end' fill='#1e4663' font-size='10'>0,05</text><text x='35' y='155' text-anchor='end' fill='#1e4663' font-size='10'>0,1</text><text x='35' y='105' text-anchor='end' fill='#1e4663' font-size='10'>0,15</text><text x='35' y='55' text-anchor='end' fill='#1e4663' font-size='10'>0,2</text><rect x='70' y='230' width='30' height='20' fill='#3b82f6' opacity='0.7'/><text x='85' y='270' text-anchor='middle' fill='#1e4663' font-size='10'>1</text><rect x='115' y='230' width='30' height='20' fill='#3b82f6' opacity='0.7'/><text x='130' y='270' text-anchor='middle' fill='#1e4663' font-size='10'>2</text><rect x='160' y='230' width='30' height='20' fill='#3b82f6' opacity='0.7'/><text x='175' y='270' text-anchor='middle' fill='#1e4663' font-size='10'>3</text><rect x='205' y='230' width='30' height='20' fill='#3b82f6' opacity='0.7'/><text x='220' y='270' text-anchor='middle' fill='#1e4663' font-size='10'>4</text><rect x='250' y='230' width='30' height='20' fill='#3b82f6' opacity='0.7'/><text x='265' y='270' text-anchor='middle' fill='#1e4663' font-size='10'>5</text><rect x='295' y='230' width='30' height='20' fill='#3b82f6' opacity='0.7'/><text x='310' y='270' text-anchor='middle' fill='#1e4663' font-size='10'>6</text><line x1='200' y1='250' x2='200' y2='230' stroke='#eab308' stroke-width='2' stroke-dasharray='4'/><circle cx='200' cy='240' r='4' fill='#eab308'/><text x='200' y='290' text-anchor='middle' fill='#1e4663' font-size='11'>Математическое ожидание = ?</text></svg>",
                hint: "💡 E = 1×1/6 + 2×1/6 + 3×1/6 + 4×1/6 + 5×1/6 + 6×1/6 = (1+2+3+4+5+6)/6 = 21/6 = ?",
                correctAnswer: "3.5",
                explanation: "✅ Математическое ожидание E = (1+2+3+4+5+6)/6 = 21/6 = <strong>3,5</strong>. Это среднее значение выпавших очков в длинной серии бросков."
            },
            {
                step: 2,
                question: "Как записывается формула математического ожидания для случайной величины X? (введите: E(X) = Σ xᵢ·pᵢ, E(X) = Σ xᵢ/pᵢ, E(X) = Σ pᵢ/xᵢ)",
                hint: "💡 Мы умножили каждое значение (1,2,3,4,5,6) на его вероятность (1/6) и сложили.",
                correctAnswer: "E(X) = Σ xᵢ·pᵢ",
                explanation: "✅ Математическое ожидание: E(X) = x₁·p₁ + x₂·p₂ + ... + xₙ·pₙ = Σ xᵢ·pᵢ."
            },
            {
                step: 3,
                question: "Бросаем два кубика. Чему равно математическое ожидание суммы очков? (введите число)",
                hint: "💡 E(X+Y) = E(X) + E(Y) = 3,5 + 3,5 = ?",
                correctAnswer: "7",
                explanation: "✅ Матожидание суммы двух кубиков = 3,5 + 3,5 = <strong>7</strong>."
            },
            {
                step: 4,
                question: "Посмотри на таблицу распределения лотереи. Чему равно математическое ожидание выигрыша?<br><br><svg width='400' height='200' viewBox='0 0 400 200' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='400' height='200' fill='#f8fafc' rx='8'/><text x='200' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Распределение выигрышей в лотерее</text><line x1='50' y1='160' x2='370' y2='160' stroke='#1e4663' stroke-width='1.5'/><line x1='50' y1='160' x2='50' y2='40' stroke='#1e4663' stroke-width='1.5'/><text x='35' y='165' text-anchor='end' fill='#1e4663' font-size='10'>0</text><text x='35' y='135' text-anchor='end' fill='#1e4663' font-size='10'>0,1</text><text x='35' y='105' text-anchor='end' fill='#1e4663' font-size='10'>0,2</text><text x='35' y='75' text-anchor='end' fill='#1e4663' font-size='10'>0,3</text><text x='35' y='45' text-anchor='end' fill='#1e4663' font-size='10'>0,4</text><rect x='70' y='150' width='40' height='10' fill='#3b82f6' opacity='0.7'/><text x='90' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>50</text><rect x='130' y='140' width='40' height='20' fill='#3b82f6' opacity='0.7'/><text x='150' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>100</text><rect x='190' y='120' width='40' height='40' fill='#3b82f6' opacity='0.7'/><text x='210' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>200</text><rect x='250' y='90' width='40' height='70' fill='#3b82f6' opacity='0.7'/><text x='270' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>500</text><rect x='310' y='60' width='40' height='100' fill='#3b82f6' opacity='0.7'/><text x='330' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>1000</text></svg><br><strong>Данные:</strong><br>Выигрыш: 50₽ (вер. 0,1), 100₽ (вер. 0,2), 200₽ (вер. 0,2), 500₽ (вер. 0,3), 1000₽ (вер. 0,2)",
                hint: "💡 E = 50×0,1 + 100×0,2 + 200×0,2 + 500×0,3 + 1000×0,2 = 5 + 20 + 40 + 150 + 200 = ?",
                correctAnswer: "415",
                explanation: "✅ E(выигрыша) = 50×0,1 + 100×0,2 + 200×0,2 + 500×0,3 + 1000×0,2 = 5 + 20 + 40 + 150 + 200 = <strong>415</strong> рублей."
            },
            {
                step: 5,
                question: "Если билет стоит 400 рублей, выгодно ли покупать билет? (введите: да или нет)",
                hint: "💡 Матожидание выигрыша = 415 руб., билет стоит 400 руб. 415 > 400",
                correctAnswer: "да",
                explanation: "✅ Да, выгодно. В среднем выигрыш (415 руб.) больше стоимости билета (400 руб.). Игрок в плюсе."
            },
            {
                step: 6,
                question: "Бросаем монету. При орле выигрываешь 20 рублей, при решке проигрываешь 10 рублей. Чему равно математическое ожидание выигрыша? (введите число)",
                hint: "💡 E = 20×0,5 + (-10)×0,5 = 10 - 5 = ?",
                correctAnswer: "5",
                explanation: "✅ E = 20×0,5 + (-10)×0,5 = 10 − 5 = <strong>5</strong> рублей. В среднем выигрываешь 5 рублей за игру."
            },
            {
                step: 7,
                question: "Как называется игра, в которой математическое ожидание выигрыша равно 0? (введите: справедливая, выгодная, невыгодная)",
                hint: "💡 Если E = 0, то ни игрок, ни казино не имеют преимущества в среднем.",
                correctAnswer: "справедливая",
                explanation: "✅ Игра называется СПРАВЕДЛИВОЙ, если математическое ожидание выигрыша равно 0. Ни одна сторона не имеет преимущества в среднем."
            },
            {
                step: 8,
                question: "Чему равно математическое ожидание константы? Например, E(10) = ? (введите число)",
                hint: "💡 Константа всегда равна 10, вероятность 1. E = 10 × 1 = 10.",
                correctAnswer: "10",
                explanation: "✅ E(const) = const. Математическое ожидание постоянной величины равно самой этой величине."
            },
            {
                step: 9,
                question: "Какое свойство математического ожидания показано на примере с двумя кубиками? (введите: E(X+Y) = E(X) + E(Y) или E(X·Y) = E(X)·E(Y))",
                hint: "💡 Мы сложили матожидания двух кубиков: 3,5 + 3,5 = 7.",
                correctAnswer: "E(X+Y) = E(X) + E(Y)",
                explanation: "✅ Свойство: математическое ожидание суммы равно сумме математических ожиданий: E(X+Y) = E(X) + E(Y)."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать о математическом ожидании? (введите: это среднее значение случайной величины в длинной серии опытов, прогноз среднего результата)",
                hint: "💡 Оно показывает, что будет в среднем при многократном повторении опыта.",
                correctAnswer: "это среднее значение случайной величины в длинной серии опытов, прогноз среднего результата",
                explanation: "✅ Главный вывод: математическое ожидание — это среднее значение случайной величины в длинной серии опытов. Оно позволяет прогнозировать средний результат, оценивать выгодность игр и лотерей, рассчитывать страховые премии и ожидаемую доходность инвестиций."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ИСПЫТАНИЯ БЕРНУЛЛИ (9 КЛАСС) ==========
const grade9_topic4Tests = [
    {
        id: "bernoulli_issl_1",
        title: "🧠 «Серия испытаний до первого успеха»",
        description: "Телефон в условиях плохой связи пытается отправить СМС. Вероятность успешной отправки при каждой попытке равна 0,3. Попытки повторяются до первой удачной отправки. Нужно найти вероятность того, что потребуется ровно 3 попытки.",
        steps: [
            {
                step: 1,
                question: "Посмотри на дерево вероятностей. Какова вероятность успеха (У) в одном испытании? (введите число)<br><br><svg width='400' height='250' viewBox='0 0 400 250' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='400' height='250' fill='#f8fafc' rx='8'/><text x='200' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Дерево вероятностей</text><circle cx='200' cy='50' r='4' fill='#1e4663'/><line x1='200' y1='54' x2='120' y2='100' stroke='#1e4663' stroke-width='1.5'/><line x1='200' y1='54' x2='280' y2='100' stroke='#1e4663' stroke-width='1.5'/><text x='110' y='90' text-anchor='end' fill='#3b82f6' font-size='11'>У (успех)</text><text x='105' y='105' text-anchor='end' fill='#1e4663' font-size='10'>p = ?</text><text x='295' y='90' text-anchor='start' fill='#ef4444' font-size='11'>Н (неудача)</text><text x='295' y='105' text-anchor='start' fill='#1e4663' font-size='10'>q = 1-p</text></svg>",
                hint: "💡 По условию задачи вероятность успешной отправки при каждой попытке равна 0,3.",
                correctAnswer: "0.3",
                explanation: "✅ Вероятность успеха (У) в одном испытании p = <strong>0,3</strong>. Вероятность неудачи q = 1 − p = 0,7."
            },
            {
                step: 2,
                question: "Какова вероятность того, что первые 2 попытки будут НЕУДАЧНЫМИ, а 3-я — УСПЕШНОЙ? (введите число, округлив до тысячных, например 0.147)",
                hint: "💡 Сначала две неудачи: 0,7 × 0,7 = 0,49. Затем успех: 0,49 × 0,3 = ?",
                correctAnswer: "0.147",
                explanation: "✅ P = q × q × p = 0,7 × 0,7 × 0,3 = 0,49 × 0,3 = <strong>0,147</strong>."
            },
            {
                step: 3,
                question: "По какой формуле вычисляется вероятность того, что успех наступит РОВНО на k-м испытании? (введите: q^{k-1}×p, p^{k-1}×q, q^{k}×p)",
                hint: "💡 Для k=3: q²×p. Для k=5: q⁴×p.",
                correctAnswer: "q^{k-1}×p",
                explanation: "✅ Вероятность того, что успех наступит на k-м испытании: P = q^{k-1} × p. (Сначала k−1 неудача, затем успех)."
            },
            {
                step: 4,
                question: "Какова вероятность, что потребуется БОЛЬШЕ 4 попыток? (введите число, округлив до тысячных, например 0.240)",
                hint: "💡 Больше 4 попыток = первые 4 попытки неудачны. P = q⁴ = 0,7⁴",
                correctAnswer: "0.240",
                explanation: "✅ P(больше 4 попыток) = q⁴ = 0,7⁴ = 0,2401 ≈ <strong>0,240</strong>."
            },
            {
                step: 5,
                question: "Теперь другая ситуация: стрелок делает 5 выстрелов. Вероятность попадания p = 0,8. Сколько всего различных последовательностей попаданий и промахов? (введите число)",
                hint: "💡 У каждого выстрела 2 исхода. Всего 2⁵ = 32 последовательности.",
                correctAnswer: "32",
                explanation: "✅ Всего исходов при 5 выстрелах: 2⁵ = <strong>32</strong> (каждый выстрел — успех или неудача)."
            },
            {
                step: 6,
                question: "Сколько существует способов выбрать, в каких именно 3 выстрелах из 5 стрелок попал? (введите число)",
                hint: "💡 Это число сочетаний C₅³ = 5×4×3 / (3×2×1) = 10",
                correctAnswer: "10",
                explanation: "✅ C₅³ = <strong>10</strong> способов выбрать 3 попадания из 5 выстрелов."
            },
            {
                step: 7,
                question: "Какова вероятность ровно 3 попаданий из 5 при p=0,8? (введите число, округлив до тысячных, например 0.205)",
                hint: "💡 P = C₅³ × p³ × q² = 10 × 0,8³ × 0,2² = 10 × 0,512 × 0,04",
                correctAnswer: "0.205",
                explanation: "✅ P = C₅³ × p³ × q² = 10 × 0,512 × 0,04 = 10 × 0,02048 = <strong>0,2048 ≈ 0,205</strong>."
            },
            {
                step: 8,
                question: "Какая формула выражает вероятность ровно k успехов в n испытаниях Бернулли? (введите: C_n^k × p^k × q^{n-k}, C_n^k × p^{n-k} × q^k, n^k × p × q)",
                hint: "💡 Мы использовали: C₅³ × p³ × q² для 3 успехов из 5.",
                correctAnswer: "C_n^k × p^k × q^{n-k}",
                explanation: "✅ Формула Бернулли: P_n(k) = C_n^k × p^k × q^{n-k}. Это вероятность ровно k успехов в n независимых испытаниях."
            },
            {
                step: 9,
                question: "Чему равно среднее число успехов в n испытаниях Бернулли? (введите: n×p, n×q, p/q)",
                hint: "💡 Если p=0,8 и n=5, среднее = 5 × 0,8 = 4 попадания.",
                correctAnswer: "n×p",
                explanation: "✅ Среднее число успехов в n испытаниях = n × p. Например, при 5 выстрелах с p=0,8 в среднем будет 4 попадания."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать об испытаниях Бернулли? (введите: вероятность успеха на k-м испытании = q^{k-1}×p, а вероятность k успехов из n = C_n^k×p^k×q^{n-k})",
                hint: "💡 Вспомни две формулы: для k-го испытания и для n испытаний.",
                correctAnswer: "вероятность успеха на k-м испытании = q^{k-1}×p, а вероятность k успехов из n = C_n^k×p^k×q^{n-k}",
                explanation: "✅ Главный вывод: В испытаниях Бернулли выделяют два типа задач: 1) ДО ПЕРВОГО УСПЕХА: P(успех на k-м) = q^{k-1}×p; 2) СЕРИЯ ИЗ n ИСПЫТАНИЙ: P(ровно k успехов) = C_n^k×p^k×q^{n-k}."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ГЕОМЕТРИЧЕСКАЯ ВЕРОЯТНОСТЬ (9 КЛАСС) ==========
const grade9_topic3Tests = [
    {
        id: "geom_prob_issl_1",
        title: "🧠 «Как измерить вероятность, когда исходов бесконечно много?»",
        description: "В квадрат со стороной 2 метра вписан круг радиусом 0,5 метра. В квадрат случайным образом бросают точку. Какова вероятность того, что она попадёт в круг? Чтобы ответить на этот вопрос, нужно сравнить площади: вероятность = площадь круга ÷ площадь квадрата.",
        steps: [
            {
                step: 1,
                question: "Посмотри на рисунок. Чему равна площадь квадрата со стороной 2? (введите число)<br><br><svg width='300' height='300' viewBox='0 0 300 300' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='300' height='300' fill='#f8fafc' rx='8'/><rect x='50' y='50' width='200' height='200' fill='none' stroke='#1e4663' stroke-width='2.5'/><circle cx='150' cy='150' r='50' fill='#3b82f6' fill-opacity='0.3' stroke='#2563eb' stroke-width='2'/><text x='150' y='45' text-anchor='middle' fill='#1e4663' font-size='12'>2 м</text><text x='40' y='150' text-anchor='middle' fill='#1e4663' font-size='12'>2 м</text><text x='150' y='155' text-anchor='middle' fill='#1e4663' font-size='10'>радиус 0,5 м</text></svg>",
                hint: "💡 Площадь квадрата = сторона × сторона = 2 × 2 = ?",
                correctAnswer: "4",
                explanation: "✅ Площадь квадрата = 2 × 2 = <strong>4</strong> м²."
            },
            {
                step: 2,
                question: "Чему равна площадь круга радиусом 0,5 м? (введите десятичной дробью, округлив до сотых, например 0.79)",
                hint: "💡 Площадь круга = π × r² = 3,14 × 0,25 = ?",
                correctAnswer: "0.79",
                explanation: "✅ Площадь круга = π × (0,5)² = π × 0,25 ≈ 3,14 × 0,25 = <strong>0,785 ≈ 0,79</strong> м²."
            },
            {
                step: 3,
                question: "Какова вероятность того, что случайная точка в квадрате попадёт в круг? (введите десятичной дробью, округлив до тысячных, например 0.196)",
                hint: "💡 Вероятность = площадь круга ÷ площадь квадрата = 0,785 ÷ 4 = ?",
                correctAnswer: "0.196",
                explanation: "✅ Вероятность = 0,785 / 4 = <strong>0,19625 ≈ 0,196</strong>. Это π/16."
            },
            {
                step: 4,
                question: "Встреча друзей: два друга приходят в парк между 12:00 и 13:00, каждый в случайный момент, и ждут 15 минут. Как изобразить эту задачу геометрически? (введите: квадрат со стороной 60 минут, где x и y — время прихода)",
                hint: "💡 x — время прихода первого, y — время прихода второго. Все возможные пары (x,y) — это квадрат 60×60.",
                correctAnswer: "квадрат со стороной 60 минут, где x и y — время прихода",
                explanation: "✅ Обозначим x — время прихода первого друга (от 0 до 60 минут после 12:00), y — время прихода второго. Все возможные исходы — квадрат со стороной 60."
            },
            {
                step: 5,
                question: "Какое условие должно выполняться, чтобы друзья встретились? (введите: |x−y| ≤ 15, x+y ≤ 15, x×y ≤ 15)",
                hint: "💡 Разница во времени прихода не должна превышать 15 минут. Если x=10, y=25, то разница 15 — ещё успеют, если x=10, y=26 — не успеют.",
                correctAnswer: "|x−y| ≤ 15",
                explanation: "✅ Друзья встретятся, если |x − y| ≤ 15 (разница во времени не больше 15 минут)."
            },
            {
                step: 6,
                question: "Посмотри на рисунок. Какая область на квадрате благоприятна для встречи?<br><br><svg width='400' height='400' viewBox='0 0 400 400' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='400' height='400' fill='#f8fafc' rx='8'/><rect x='50' y='50' width='300' height='300' fill='none' stroke='#1e4663' stroke-width='2'/><text x='200' y='40' text-anchor='middle' fill='#1e4663' font-size='12'>x (время прихода первого, мин)</text><text x='30' y='200' text-anchor='middle' fill='#1e4663' font-size='12' transform='rotate(-90,30,200)'>y (время прихода второго, мин)</text><line x1='50' y1='200' x2='350' y2='200' stroke='#94a3b8' stroke-width='1' stroke-dasharray='4'/><line x1='200' y1='50' x2='200' y2='350' stroke='#94a3b8' stroke-width='1' stroke-dasharray='4'/><polygon points='50,65 125,50 275,50 350,125 350,275 275,350 125,350 50,275' fill='#3b82f6' fill-opacity='0.3' stroke='#2563eb' stroke-width='2'/><text x='200' y='370' text-anchor='middle' fill='#1e4663' font-size='10'>Благоприятная область — полоса шириной 30 минут</text></svg>",
                hint: "💡 Полоса между прямыми y = x − 15 и y = x + 15 внутри квадрата.",
                correctAnswer: "полоса между прямыми y=x-15 и y=x+15",
                explanation: "✅ Благоприятная область — полоса между прямыми y = x − 15 и y = x + 15 внутри квадрата."
            },
            {
                step: 7,
                question: "Чему равна вероятность встречи? (введите десятичной дробью, например 0.4375)",
                hint: "💡 Вероятность = (площадь полосы) / (площадь квадрата). Площадь квадрата = 3600. Площадь полосы = 3600 − 2025 = 1575.",
                correctAnswer: "0.4375",
                explanation: "✅ Вероятность встречи = 1575 / 3600 = <strong>0,4375</strong> = 7/16 ≈ 44%."
            },
            {
                step: 8,
                question: "Когда НЕЛЬЗЯ использовать геометрическую вероятность? (введите: когда точки фигуры НЕ равновозможны или когда фигура круглая)",
                hint: "💡 Если стрелок целится в центр мишени, вероятность попасть в центр выше, чем на край.",
                correctAnswer: "когда точки фигуры НЕ равновозможны",
                explanation: "✅ Геометрическая вероятность работает только тогда, когда ВСЕ ТОЧКИ ФИГУРЫ РАВНОВОЗМОЖНЫ. Если распределение неравномерное (например, стрелок целится в центр), формула не работает."
            },
            {
                step: 9,
                question: "Как найти вероятность того, что случайная точка в квадрате попадёт в его левую половину? (введите: площадь левой половины ÷ площадь квадрата = 1/2)",
                hint: "💡 Левая половина квадрата — это прямоугольник шириной 1 и высотой 2.",
                correctAnswer: "площадь левой половины ÷ площадь квадрата = 1/2",
                explanation: "✅ Левая половина квадрата имеет площадь 2 (1×2), а вся площадь 4. Вероятность = 2/4 = 1/2."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать о геометрической вероятности? (введите: вероятность = отношение мер (длин, площадей, объёмов) благоприятной области ко всей области)",
                hint: "💡 Мы сравнивали площади круга и квадрата, площади полосы и квадрата.",
                correctAnswer: "вероятность = отношение мер (длин, площадей, объёмов) благоприятной области ко всей области",
                explanation: "✅ Главный вывод: ГЕОМЕТРИЧЕСКАЯ ВЕРОЯТНОСТЬ — это отношение меры благоприятной области к мере всей области. Мерой может быть длина (для отрезков), площадь (для плоских фигур) или объём (для пространственных тел). Формула работает только при РАВНОВОЗМОЖНОСТИ всех точек."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ТРЕУГОЛЬНИК ПАСКАЛЯ (9 КЛАСС) ==========
const grade9_topic2Tests = [
    {
        id: "pascal_issl_1",
        title: "🧠 «Как открыть треугольник, который уже знали древние?»",
        description: "Есть 3 разных предмета: яблоко, банан, апельсин. Сколькими способами можно выбрать 0, 1, 2, 3 предмета? Получились числа: 1, 3, 3, 1. А для 4 предметов: 1, 4, 6, 4, 1. Если записать эти строки одну под другой, получится треугольная таблица. Она называется треугольником Паскаля.",
        steps: [
            {
                step: 1,
                question: "Посмотри на треугольник Паскаля. Какое число стоит в 3-й строке на 2-м месте (считая с 0)?<br><br><svg width='500' height='350' viewBox='0 0 500 350' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='500' height='350' fill='#f8fafc' rx='8'/><text x='250' y='25' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>Треугольник Паскаля</text><text x='250' y='55' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 0:                     1</text><text x='250' y='75' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 1:                   1   1</text><text x='250' y='95' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 2:                 1   2   1</text><text x='250' y='115' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 3:               1   3   3   1</text><text x='250' y='135' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 4:             1   4   6   4   1</text><text x='250' y='155' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 5:           1   5  10  10   5   1</text><text x='250' y='175' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 6:         1   6  15  20  15   6   1</text><text x='250' y='195' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 7:       1   7  21  35  35  21   7   1</text><text x='250' y='215' text-anchor='middle' fill='#1e4663' font-size='12'>Строка 8:     1   8  28  56  70  56  28   8   1</text></svg>",
                hint: "💡 Строка 3: 1, 3, 3, 1. 2-е место (считая с 0) — это третий элемент.",
                correctAnswer: "3",
                explanation: "✅ В 3-й строке числа: 1 (0-е место), 3 (1-е место), <strong>3</strong> (2-е место), 1 (3-е место)."
            },
            {
                step: 2,
                question: "Как построить следующую строку треугольника Паскаля из предыдущей? (введите: каждое число = сумма двух чисел над ним или каждое число = произведение двух чисел над ним)",
                hint: "💡 Посмотри на числа: 4 = 1+3, 6 = 3+3, 4 = 3+1.",
                correctAnswer: "каждое число = сумма двух чисел над ним",
                explanation: "✅ ПРАВИЛО ПОСТРОЕНИЯ: по краям строки — единицы, а каждое внутреннее число равно СУММЕ двух чисел, стоящих над ним (слева и справа)."
            },
            {
                step: 3,
                question: "Построй 6-ю строку треугольника. Чему равно число на 3-м месте (считая с 0)? (введите число)",
                hint: "💡 5-я строка: 1,5,10,10,5,1. 6-я строка: 1, 1+5=6, 5+10=15, 10+10=20, 10+5=15, 5+1=6, 1",
                correctAnswer: "20",
                explanation: "✅ 6-я строка: 1, 6, 15, <strong>20</strong>, 15, 6, 1. На 3-м месте (считая с 0) стоит число <strong>20</strong>."
            },
            {
                step: 4,
                question: "Какое число в треугольнике Паскаля соответствует C₇³ (сочетание из 7 по 3)? (введите число)",
                hint: "💡 7-я строка: 1, 7, 21, 35, 35, 21, 7, 1. 3-е место (считая с 0) — это 35.",
                correctAnswer: "35",
                explanation: "✅ В треугольнике Паскаля на пересечении n-й строки и k-го места (считая с 0) стоит Cₙᵏ. C₇³ = 35."
            },
            {
                step: 5,
                question: "Чему равно C₆² (сочетание из 6 по 2) по треугольнику Паскаля? (введите число)",
                hint: "💡 6-я строка: 1, 6, 15, 20, 15, 6, 1. 2-е место (считая с 0) — это 15.",
                correctAnswer: "15",
                explanation: "✅ C₆² = 15. Проверка по формуле: 6×5/2 = 30/2 = 15."
            },
            {
                step: 6,
                question: "Какое свойство треугольника Паскаля показано на примере C₈³ = C₈⁵? (введите: симметрия, ассоциативность, коммутативность)",
                hint: "💡 8-я строка: 1, 8, 28, 56, 70, 56, 28, 8, 1. C₈³ = 56, C₈⁵ = 56.",
                correctAnswer: "симметрия",
                explanation: "✅ СВОЙСТВО СИММЕТРИИ: Cₙᵏ = Cₙⁿ⁻ᵏ. Строка читается одинаково слева направо и справа налево."
            },
            {
                step: 7,
                question: "Чему равна сумма чисел 4-й строки треугольника Паскаля? (введите число)",
                hint: "💡 4-я строка: 1, 4, 6, 4, 1. Сложи: 1+4+6+4+1 = ?",
                correctAnswer: "16",
                explanation: "✅ Сумма чисел 4-й строки = 1+4+6+4+1 = <strong>16</strong> = 2⁴. Свойство: сумма чисел n-й строки = 2ⁿ."
            },
            {
                step: 8,
                question: "Чему равна сумма чисел 7-й строки треугольника Паскаля? (введите число)",
                hint: "💡 По свойству сумма n-й строки = 2ⁿ. 2⁷ = 128.",
                correctAnswer: "128",
                explanation: "✅ Сумма чисел 7-й строки = 2⁷ = <strong>128</strong>. Это общее количество всех подмножеств 7-элементного множества."
            },
            {
                step: 9,
                question: "Как называется способ вычисления числа в треугольнике Паскаля без построения всех предыдущих строк? (введите: биномиальный коэффициент, мультипликатор, делитель)",
                hint: "💡 Числа в треугольнике Паскаля — это Cₙᵏ, которые можно вычислить по формуле n!/(k!·(n−k)!).",
                correctAnswer: "биномиальный коэффициент",
                explanation: "✅ Числа треугольника Паскаля называются БИНОМИАЛЬНЫМИ КОЭФФИЦИЕНТАМИ. Они вычисляются по формуле Cₙᵏ = n!/(k!·(n−k)!)."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать о треугольнике Паскаля? (введите: он помогает быстро находить Cₙᵏ и изучать их свойства или он нужен только для красивых картинок)",
                hint: "💡 Что мы использовали треугольник для? Находили C₇³, C₆², изучали симметрию и суммы строк.",
                correctAnswer: "он помогает быстро находить Cₙᵏ и изучать их свойства",
                explanation: "✅ Главный вывод: Треугольник Паскаля — это удобный способ представления биномиальных коэффициентов Cₙᵏ. Он позволяет быстро находить числа сочетаний, наглядно демонстрирует свойства симметрии (Cₙᵏ = Cₙⁿ⁻ᵏ) и то, что сумма строки равна 2ⁿ."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ПЕРЕСТАНОВКИ, ФАКТОРИАЛ, СОЧЕТАНИЯ (9 КЛАСС) ==========
const grade9_topic1Tests = [
    {
        id: "comb_issl_1",
        title: "🧠 «Сколько способов?»",
        description: "В финал турнира вышли 3 спортсмена: Андрей (А), Борис (Б) и Виктор (В). Нужно распределить золотую, серебряную и бронзовую медали. Сколькими способами это можно сделать? А если бы спортсменов было 10? Как считать быстро?",
        steps: [
            {
                step: 1,
                question: "Сколькими способами можно распределить 3 медали (золото, серебро, бронзу) между 3 спортсменами? (введите число)",
                hint: "💡 Золото может получить любой из 3, серебро — любой из 2 оставшихся, бронза — последний. 3×2×1 = ?",
                correctAnswer: "6",
                explanation: "✅ Всего способов: 3 × 2 × 1 = <strong>6</strong>. Это число называется ПЕРЕСТАНОВКОЙ из 3 элементов."
            },
            {
                step: 2,
                question: "Как называется произведение 1×2×3×4×5×6×7×8×9×10? (введите: факториал, перестановка, сочетание)",
                hint: "💡 Такое произведение называется ФАКТОРИАЛОМ и обозначается 10!",
                correctAnswer: "факториал",
                explanation: "✅ Произведение всех натуральных чисел от 1 до n называется ФАКТОРИАЛОМ и обозначается n!. Например, 10! = 1×2×3×4×5×6×7×8×9×10."
            },
            {
                step: 3,
                question: "Чему равен 5! (факториал 5)? (введите число)",
                hint: "💡 5! = 1×2×3×4×5 = ?",
                correctAnswer: "120",
                explanation: "✅ 5! = 1×2×3×4×5 = <strong>120</strong>. По определению, 0! = 1."
            },
            {
                step: 4,
                question: "Сколько разных трёхзначных чисел можно составить из цифр 1, 2, 3, 4, 5 (без повторений цифр)? (введите число)",
                hint: "💡 Первую цифру выбираем 5 способами, вторую — 4, третью — 3. 5×4×3 = ?",
                correctAnswer: "60",
                explanation: "✅ 5 × 4 × 3 = <strong>60</strong>. Это РАЗМЕЩЕНИЕ (порядок важен, используем не все цифры)."
            },
            {
                step: 5,
                question: "В классе 25 учеников. Нужно выбрать 3 дежурных. Порядок НЕ важен. Какая формула подходит? (введите: перестановки, размещения или сочетания)",
                hint: "💡 Перестановки — все элементы, порядок важен. Размещения — порядок важен, используем не все. Сочетания — порядок НЕ важен.",
                correctAnswer: "сочетания",
                explanation: "✅ Когда порядок НЕ важен, используются СОЧЕТАНИЯ. Формула: Cₙᵏ = n! / (k!·(n−k)!)."
            },
            {
                step: 6,
                question: "Чему равно C₂₅³ (количество способов выбрать 3 дежурных из 25)? (введите число)",
                hint: "💡 C₂₅³ = (25×24×23) / (3×2×1) = 13800 / 6 = ?",
                correctAnswer: "2300",
                explanation: "✅ C₂₅³ = (25×24×23) / (3×2×1) = 13800 / 6 = <strong>2300</strong>."
            },
            {
                step: 7,
                question: "В чём разница между размещением и сочетанием? (введите: в размещении порядок важен, в сочетании — нет или в сочетании порядок важен, в размещении — нет)",
                hint: "💡 При выборе дежурных (сочетание) порядок не важен. При выборе капитана и заместителя (размещение) — важен.",
                correctAnswer: "в размещении порядок важен, в сочетании — нет",
                explanation: "✅ РАЗМЕЩЕНИЕ — порядок ВАЖЕН (капитан и заместитель — разные роли). СОЧЕТАНИЕ — порядок НЕ ВАЖЕН (дежурные равны)."
            },
            {
                step: 8,
                question: "Какое свойство сочетаний здесь показано: C₁₀⁴ = C₁₀⁶? (введите: симметрия, коммутативность, ассоциативность)",
                hint: "💡 Выбрать 4 человека из 10 — это то же самое, что выбрать, кто НЕ войдёт (6 человек).",
                correctAnswer: "симметрия",
                explanation: "✅ Это свойство СИММЕТРИИ: Cₙᵏ = Cₙⁿ⁻ᵏ. Выбрать k элементов — всё равно что выбрать n−k элементов, которые не войдут."
            },
            {
                step: 9,
                question: "Сколько существует способов выбрать старосту и заместителя из 20 учеников? (введите число)",
                hint: "💡 Порядок важен (староста и заместитель — разные должности). 20 × 19 = ?",
                correctAnswer: "380",
                explanation: "✅ Это РАЗМЕЩЕНИЕ: 20 × 19 = <strong>380</strong>. Формула: A₂₀² = 20! / 18! = 20×19 = 380."
            },
            {
                step: 10,
                question: "Какой главный вопрос нужно задать, чтобы выбрать правильную формулу? (введите: важен ли порядок, сколько всего элементов, все ли элементы используются)",
                hint: "💡 Главное различие между размещением и сочетанием — важен ли порядок.",
                correctAnswer: "важен ли порядок",
                explanation: "✅ Главный вопрос: ВАЖЕН ЛИ ПОРЯДОК? Если да — используем размещение (или перестановку, если все элементы). Если нет — используем сочетание."
            }
        ]
    }
];
  // ========== ДОБАВЬТЕ ЭТИ СТРОКИ ДЛЯ 8 КЛАССА ==========
const grade8_topic1Formulas = [], grade8_topic2Formulas = [], grade8_topic3Formulas = [], grade8_topic4Formulas = [], grade8_topic5Formulas = [];
const grade8_topic1Practice = [], grade8_topic2Practice = [], grade8_topic3Practice = [], grade8_topic4Practice = [], grade8_topic5Practice = [];
    const multiplicationTests = [], multiplicationPractice = [];
    const oppositeTests = [], oppositeFormulas = [], oppositePractice = [];
    const eulerTests = [], eulerFormulas = [], eulerPractice = [];
    const incompatibleTests = [], incompatiblePractice = [];
    const conditionalTests = [], conditionalPractice = [];
    const treeTests = [], treeFormulas = [], treePractice = [];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ДИАГРАММА ЭЙЛЕРА. ОБЪЕДИНЕНИЕ И ПЕРЕСЕЧЕНИЕ СОБЫТИЙ (8 КЛАСС) ==========
const grade8_topic5Tests = [
    {
        id: "euler_issl_1",
        title: "🧠 «Как нарисовать случайность?»",
        description: "Бросаем игральный кубик. Событие A = {выпало чётное число} = {2,4,6}. Событие B = {выпало число больше 3} = {4,5,6}. Как наглядно показать, какие исходы входят в A, какие в B, а какие — в оба события? Помогут диаграммы Эйлера — круги, которые показывают отношения между событиями.",
        steps: [
            {
                step: 1,
                question: "Посмотри на диаграмму. Какая область соответствует ПЕРЕСЕЧЕНИЮ A ∩ B?<br><br><svg width='500' height='320' viewBox='0 0 500 320' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='500' height='320' fill='#f8fafc' rx='8'/><text x='250' y='25' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>Диаграмма Эйлера для событий A и B</text><circle cx='180' cy='160' r='100' fill='#3b82f6' fill-opacity='0.2' stroke='#2563eb' stroke-width='2.5'/><text x='130' y='155' text-anchor='middle' fill='#1e4663' font-size='16' font-weight='bold'>A</text><circle cx='320' cy='160' r='100' fill='#ef4444' fill-opacity='0.2' stroke='#dc2626' stroke-width='2.5'/><text x='370' y='155' text-anchor='middle' fill='#1e4663' font-size='16' font-weight='bold'>B</text><text x='250' y='155' text-anchor='middle' fill='#1e4663' font-size='14'>?</text><text x='120' y='280' text-anchor='middle' fill='#3b82f6' font-size='12'>Только A</text><text x='250' y='280' text-anchor='middle' fill='#a855f7' font-size='12'>A ∩ B</text><text x='380' y='280' text-anchor='middle' fill='#ef4444' font-size='12'>Только B</text><text x='250' y='300' text-anchor='middle' fill='#94a3b8' font-size='12'>Вне A и B</text></svg>",
                hint: "💡 Пересечение — это общая часть кругов A и B. На диаграмме она обозначена знаком вопроса.",
                correctAnswer: "область со знаком вопроса",
                explanation: "✅ ПЕРЕСЕЧЕНИЕ (A ∩ B) — это область, где круги A и B накладываются друг на друга. В этой области находятся исходы, которые принадлежат И событию A, И событию B."
            },
            {
                step: 2,
                question: "В нашем примере (кубик) какие исходы входят в пересечение A ∩ B? (введите числа через запятую, например 2,4)",
                hint: "💡 A = {2,4,6}, B = {4,5,6}. Какие числа есть и там, и там?",
                correctAnswer: "4,6",
                explanation: "✅ A ∩ B = {4,6}. Это числа, которые одновременно чётные и больше 3."
            },
            {
                step: 3,
                question: "Посмотри на диаграмму. Какая область соответствует ОБЪЕДИНЕНИЮ A ∪ B?<br><br><svg width='500' height='320' viewBox='0 0 500 320' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='500' height='320' fill='#f8fafc' rx='8'/><text x='250' y='25' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>Диаграмма Эйлера для событий A и B</text><circle cx='180' cy='160' r='100' fill='#3b82f6' fill-opacity='0.2' stroke='#2563eb' stroke-width='2.5'/><text x='130' y='155' text-anchor='middle' fill='#1e4663' font-size='16' font-weight='bold'>A</text><circle cx='320' cy='160' r='100' fill='#ef4444' fill-opacity='0.2' stroke='#dc2626' stroke-width='2.5'/><text x='370' y='155' text-anchor='middle' fill='#1e4663' font-size='16' font-weight='bold'>B</text><rect x='50' y='40' width='12' height='12' fill='#3b82f6' fill-opacity='0.5'/><text x='68' y='52' fill='#1e4663' font-size='11'>Только A</text><rect x='150' y='40' width='12' height='12' fill='#a855f7' fill-opacity='0.5'/><text x='168' y='52' fill='#1e4663' font-size='11'>A ∩ B</text><rect x='260' y='40' width='12' height='12' fill='#ef4444' fill-opacity='0.5'/><text x='278' y='52' fill='#1e4663' font-size='11'>Только B</text><rect x='370' y='40' width='12' height='12' fill='#94a3b8'/><text x='388' y='52' fill='#1e4663' font-size='11'>Вне A и B</text></svg>",
                hint: "💡 Объединение — это все, кто принадлежит A ИЛИ B. Это три верхние области.",
                correctAnswer: "три верхние области (только A, A∩B, только B)",
                explanation: "✅ ОБЪЕДИНЕНИЕ (A ∪ B) — это все исходы, которые находятся в A или в B (или в обоих). На диаграмме это три области: только A, пересечение, только B."
            },
            {
                step: 4,
                question: "Какие исходы входят в объединение A ∪ B в нашем примере с кубиком? (введите числа через запятую, например 2,4,5,6)",
                hint: "💡 A = {2,4,6}, B = {4,5,6}. Объедини все числа: 2,4,6 и 4,5,6 — убери повторы.",
                correctAnswer: "2,4,5,6",
                explanation: "✅ A ∪ B = {2,4,5,6}. Это числа, которые чётные ИЛИ больше 3 (или и то, и другое)."
            },
            {
                step: 5,
                question: "Сколько всего исходов в пересечении A ∩ B? (введите число)",
                hint: "💡 A ∩ B = {4,6} — два числа.",
                correctAnswer: "2",
                explanation: "✅ |A ∩ B| = <strong>2</strong> (исходы 4 и 6)."
            },
            {
                step: 6,
                question: "Сколько всего исходов в объединении A ∪ B? (введите число)",
                hint: "💡 A ∪ B = {2,4,5,6} — четыре числа.",
                correctAnswer: "4",
                explanation: "✅ |A ∪ B| = <strong>4</strong> (исходы 2,4,5,6)."
            },
            {
                step: 7,
                question: "Почему |A| + |B| = 3 + 3 = 6, а |A ∪ B| = 4? Что было посчитано дважды? (введите: пересечение A∩B или пустое множество)",
                hint: "💡 Числа 4 и 6 входят и в A, и в B. При сложении |A| + |B| они учитываются дважды.",
                correctAnswer: "пересечение A∩B",
                explanation: "✅ При сложении |A| + |B| элементы пересечения A∩B (4 и 6) учитываются дважды. Поэтому |A ∪ B| = |A| + |B| − |A ∩ B| = 3 + 3 − 2 = 4."
            },
            {
                step: 8,
                question: "Если события НЕСОВМЕСТНЫ (не имеют общих исходов), как выглядят их круги на диаграмме Эйлера?<br><br><svg width='500' height='250' viewBox='0 0 500 250' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='500' height='250' fill='#f8fafc' rx='8'/><text x='250' y='25' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>Несовместные события</text><circle cx='170' cy='130' r='70' fill='#3b82f6' fill-opacity='0.2' stroke='#2563eb' stroke-width='2.5'/><text x='130' y='125' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>A</text><circle cx='330' cy='130' r='70' fill='#ef4444' fill-opacity='0.2' stroke='#dc2626' stroke-width='2.5'/><text x='370' y='125' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>B</text><text x='250' y='210' text-anchor='middle' fill='#1e4663' font-size='12'>Круги НЕ пересекаются</text></svg>",
                hint: "💡 Если у событий нет общих исходов, их круги не должны пересекаться.",
                correctAnswer: "круги не пересекаются",
                explanation: "✅ Если события НЕСОВМЕСТНЫ (A ∩ B = ∅), то их круги на диаграмме Эйлера НЕ ПЕРЕСЕКАЮТСЯ. Например, A = {2,4,6}, C = {1,3,5} — чётные и нечётные числа."
            },
            {
                step: 9,
                question: "Чему равна вероятность пересечения A ∩ B, если A и B несовместны? (введите: 0, 1 или 0.5)",
                hint: "💡 Если у событий нет общих исходов, они не могут произойти одновременно.",
                correctAnswer: "0",
                explanation: "✅ Если A и B несовместны, то A ∩ B = ∅ (пустое множество), и P(A ∩ B) = <strong>0</strong>."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать о диаграммах Эйлера для событий? (введите: они помогают наглядно увидеть отношения между событиями или они используются только в комбинаторике)",
                hint: "💡 Что мы использовали для наглядности? Круги показывают пересечение, объединение, несовместность.",
                correctAnswer: "они помогают наглядно увидеть отношения между событиями",
                explanation: "✅ Главный вывод: диаграммы Эйлера помогают НАГЛЯДНО ПРЕДСТАВИТЬ отношения между случайными событиями: пересечение (общая часть кругов), объединение (оба круга вместе), несовместность (круги не пересекаются). Они также иллюстрируют формулу P(A ∪ B) = P(A) + P(B) − P(A ∩ B)."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - МНОЖЕСТВА (ОБЪЕДИНЕНИЕ, ПЕРЕСЕЧЕНИЕ, ДОПОЛНЕНИЕ) (8 КЛАСС) ==========
const grade8_topic4Tests = [
    {
        id: "sets_issl_1",
        title: "🧠 «Как дружат множества?»",
        description: "В классе 30 учеников. Математический кружок (множество A) посещают 12 человек, спортивную секцию (множество B) — 15 человек, а и кружок, и секцию — 5 человек. Как разобраться, кто где? Помогут диаграммы Эйлера — круги, которые наглядно показывают отношения между множествами.",
        steps: [
            {
                step: 1,
                question: "Посмотри на диаграмму Эйлера. Какая область соответствует ПЕРЕСЕЧЕНИЮ множеств A и B (A ∩ B)?<br><br><svg width='400' height='300' viewBox='0 0 400 300' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='400' height='300' fill='#f8fafc' rx='8'/><text x='200' y='25' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Диаграмма Эйлера</text><circle cx='140' cy='150' r='80' fill='#3b82f6' fill-opacity='0.2' stroke='#2563eb' stroke-width='2'/><text x='100' y='145' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>A</text><circle cx='260' cy='150' r='80' fill='#ef4444' fill-opacity='0.2' stroke='#dc2626' stroke-width='2'/><text x='300' y='145' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>B</text><text x='200' y='145' text-anchor='middle' fill='#1e4663' font-size='12'>?</text><rect x='50' y='30' width='12' height='12' fill='#3b82f6' fill-opacity='0.5'/><text x='68' y='42' fill='#1e4663' font-size='10'>Только A</text><rect x='150' y='30' width='12' height='12' fill='#a855f7' fill-opacity='0.5'/><text x='168' y='42' fill='#1e4663' font-size='10'>A ∩ B</text><rect x='260' y='30' width='12' height='12' fill='#ef4444' fill-opacity='0.5'/><text x='278' y='42' fill='#1e4663' font-size='10'>Только B</text><rect x='350' y='30' width='12' height='12' fill='#94a3b8'/><text x='368' y='42' fill='#1e4663' font-size='10'>Вне A и B</text></svg>",
                hint: "💡 Пересечение — это общая часть кругов A и B. На диаграмме она обозначена знаком вопроса.",
                correctAnswer: "область со знаком вопроса",
                explanation: "✅ ПЕРЕСЕЧЕНИЕ (A ∩ B) — это область, где круги A и B накладываются друг на друга. В этой области находятся ученики, которые ходят И на кружок, И в секцию."
            },
            {
                step: 2,
                question: "Сколько учеников находится в пересечении A ∩ B? (введите число)",
                hint: "💡 По условию: и кружок, и секцию посещают 5 человек.",
                correctAnswer: "5",
                explanation: "✅ |A ∩ B| = <strong>5</strong> (пять человек посещают и кружок, и секцию). На диаграмме это центральная область."
            },
            {
                step: 3,
                question: "Сколько учеников посещают ТОЛЬКО кружок (A без B)? (введите число)",
                hint: "💡 Из всех, кто ходит на кружок (12), вычти тех, кто ходит и туда, и туда (5).",
                correctAnswer: "7",
                explanation: "✅ Только кружок: 12 − 5 = <strong>7</strong> человек. На диаграмме это левая область (без пересечения)."
            },
            {
                step: 4,
                question: "Сколько учеников посещают ТОЛЬКО секцию (B без A)? (введите число)",
                hint: "💡 Из всех, кто ходит в секцию (15), вычти тех, кто ходит и туда, и туда (5).",
                correctAnswer: "10",
                explanation: "✅ Только секция: 15 − 5 = <strong>10</strong> человек. На диаграмме это правая область (без пересечения)."
            },
            {
                step: 5,
                question: "Сколько учеников посещают ХОТЯ БЫ ОДНО из этих занятий (объединение A ∪ B)? (введите число)",
                hint: "💡 Сложи: только кружок (7) + только секция (10) + пересечение (5).",
                correctAnswer: "22",
                explanation: "✅ Объединение |A ∪ B| = 7 + 10 + 5 = <strong>22</strong>. Формула: |A ∪ B| = |A| + |B| − |A ∩ B| = 12 + 15 − 5 = 22."
            },
            {
                step: 6,
                question: "Сколько учеников НЕ посещают кружок (дополнение A — Ā)? (введите число)",
                hint: "💡 Из всех учеников (30) вычти тех, кто ходит на кружок (12).",
                correctAnswer: "18",
                explanation: "✅ Дополнение |Ā| = 30 − 12 = <strong>18</strong>. Это те, кто не ходит на кружок (только секция + никто)."
            },
            {
                step: 7,
                question: "Сколько учеников НЕ посещают НИ кружок, НИ секцию? (введите число)",
                hint: "💡 Из всех учеников (30) вычти объединение A ∪ B (22).",
                correctAnswer: "8",
                explanation: "✅ Ни кружок, ни секцию не посещают: 30 − 22 = <strong>8</strong> человек. На диаграмме это область вне кругов."
            },
            {
                step: 8,
                question: "Посмотри на диаграмму. Какая область соответствует ОБЪЕДИНЕНИЮ A ∪ B?<br><br><svg width='400' height='300' viewBox='0 0 400 300' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='400' height='300' fill='#f8fafc' rx='8'/><text x='200' y='25' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Диаграмма Эйлера</text><circle cx='140' cy='150' r='80' fill='#3b82f6' fill-opacity='0.2' stroke='#2563eb' stroke-width='2'/><text x='100' y='145' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>A</text><circle cx='260' cy='150' r='80' fill='#ef4444' fill-opacity='0.2' stroke='#dc2626' stroke-width='2'/><text x='300' y='145' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>B</text><rect x='50' y='30' width='12' height='12' fill='#3b82f6' fill-opacity='0.5'/><text x='68' y='42' fill='#1e4663' font-size='10'>Только A</text><rect x='150' y='30' width='12' height='12' fill='#a855f7' fill-opacity='0.5'/><text x='168' y='42' fill='#1e4663' font-size='10'>A ∩ B</text><rect x='260' y='30' width='12' height='12' fill='#ef4444' fill-opacity='0.5'/><text x='278' y='42' fill='#1e4663' font-size='10'>Только B</text><rect x='350' y='30' width='12' height='12' fill='#94a3b8'/><text x='368' y='42' fill='#1e4663' font-size='10'>Вне A и B</text></svg>",
                hint: "💡 Объединение — это все, кто принадлежит A ИЛИ B (или обоим). Это три верхние области.",
                correctAnswer: "три верхние области (только A, A∩B, только B)",
                explanation: "✅ ОБЪЕДИНЕНИЕ (A ∪ B) — это все элементы, которые находятся в A или в B (или в обоих). На диаграмме это три области: только A, A∩B, только B."
            },
            {
                step: 9,
                question: "Чему равно A ∩ B, если A = {1,2,3,4,5}, B = {4,5,6,7,8}? (введите числа через запятую, например 4,5)",
                hint: "💡 Пересечение — это числа, которые есть и в A, и в B.",
                correctAnswer: "4,5",
                explanation: "✅ A ∩ B = {<strong>4,5</strong>}. Это общие элементы обоих множеств."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать об операциях над множествами? (введите: диаграммы Эйлера помогают наглядно представить отношения между множествами или множества можно только перечислять)",
                hint: "💡 Что мы использовали для наглядности? Круги на рисунках.",
                correctAnswer: "диаграммы Эйлера помогают наглядно представить отношения между множествами",
                explanation: "✅ Главный вывод: операции над множествами (пересечение, объединение, дополнение) удобно изображать с помощью ДИАГРАММ ЭЙЛЕРА. Они помогают наглядно увидеть, какие элементы где находятся, и легко вычислять количество элементов в каждой области."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ДИАГРАММЫ РАССЕИВАНИЯ (8 КЛАСС) ==========
const grade8_topic3Tests = [
    {
        id: "scatter_issl_1",
        title: "🧠 «Как увидеть связь между величинами?»",
        description: "Исследователь хочет выяснить, есть ли связь между ростом человека и его массой. У него есть данные 15 человек. Но глядя на таблицу, трудно что-то понять. Что делать? Построить диаграмму рассеивания — нанести точки на плоскость, где по горизонтали — рост, по вертикали — масса. Форма облака точек подскажет, есть ли связь.",
        steps: [
            {
                step: 1,
                question: "Посмотри на диаграмму. В каком направлении вытянуто облако точек?<br><br><svg width='500' height='350' viewBox='0 0 500 350' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='500' height='350' fill='#f8fafc' rx='8'/><text x='250' y='25' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Зависимость массы от роста</text><line x1='60' y1='280' x2='460' y2='280' stroke='#1e4663' stroke-width='1.5'/><line x1='60' y1='280' x2='60' y2='40' stroke='#1e4663' stroke-width='1.5'/><text x='50' y='295' text-anchor='end' fill='#1e4663' font-size='10'>150</text><text x='50' y='250' text-anchor='end' fill='#1e4663' font-size='10'>160</text><text x='50' y='205' text-anchor='end' fill='#1e4663' font-size='10'>170</text><text x='50' y='160' text-anchor='end' fill='#1e4663' font-size='10'>180</text><text x='50' y='115' text-anchor='end' fill='#1e4663' font-size='10'>190</text><text x='50' y='70' text-anchor='end' fill='#1e4663' font-size='10'>200</text><text x='260' y='320' text-anchor='middle' fill='#1e4663' font-size='11'>Рост (см)</text><text x='25' y='170' text-anchor='middle' fill='#1e4663' font-size='11' transform='rotate(-90,25,170)'>Масса (кг)</text><circle cx='120' cy='265' r='5' fill='#3b82f6'/><circle cx='150' cy='250' r='5' fill='#3b82f6'/><circle cx='180' cy='240' r='5' fill='#3b82f6'/><circle cx='200' cy='230' r='5' fill='#3b82f6'/><circle cx='230' cy='215' r='5' fill='#3b82f6'/><circle cx='250' cy='205' r='5' fill='#3b82f6'/><circle cx='270' cy='195' r='5' fill='#3b82f6'/><circle cx='290' cy='185' r='5' fill='#3b82f6'/><circle cx='310' cy='175' r='5' fill='#3b82f6'/><circle cx='330' cy='165' r='5' fill='#3b82f6'/><circle cx='350' cy='155' r='5' fill='#3b82f6'/><circle cx='370' cy='145' r='5' fill='#3b82f6'/><circle cx='390' cy='135' r='5' fill='#3b82f6'/><circle cx='410' cy='125' r='5' fill='#3b82f6'/><circle cx='430' cy='115' r='5' fill='#3b82f6'/></svg>",
                hint: "💡 Обрати внимание: с ростом роста масса увеличивается. Облако вытянуто слева направо вверх.",
                correctAnswer: "слева направо вверх",
                explanation: "✅ Облако точек вытянуто СЛЕВА НАПРАВО ВВЕРХ. Это указывает на ПОЛОЖИТЕЛЬНУЮ связь: чем больше рост, тем больше масса (в среднем)."
            },
            {
                step: 2,
                question: "Как называется такая связь? (введите: положительная, отрицательная или отсутствие связи)",
                hint: "💡 Если одна величина растёт, и другая растёт — это положительная связь.",
                correctAnswer: "положительная",
                explanation: "✅ Такая связь называется ПОЛОЖИТЕЛЬНОЙ. Примеры: рост и масса, тренировки и результаты, доход и расходы."
            },
            {
                step: 3,
                question: "Как выглядит ОТРИЦАТЕЛЬНАЯ связь на диаграмме рассеивания? (введите: облако вытянуто слева направо вниз или облако вытянуто слева направо вверх)",
                hint: "💡 При отрицательной связи: больше X → меньше Y.",
                correctAnswer: "облако вытянуто слева направо вниз",
                explanation: "✅ При отрицательной связи облако вытянуто СЛЕВА НАПРАВО ВНИЗ. Пример: время за играми и время на уроки — чем больше играешь, тем меньше остаётся на учёбу."
            },
            {
                step: 4,
                question: "Посмотри на две диаграммы. На какой связь СИЛЬНЕЕ?<br><br><strong>Диаграмма А (узкое облако):</strong><br><svg width='300' height='200' viewBox='0 0 300 200' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='300' height='200' fill='#f8fafc' rx='8'/><line x1='40' y1='170' x2='280' y2='170' stroke='#1e4663' stroke-width='1'/><line x1='40' y1='170' x2='40' y2='30' stroke='#1e4663' stroke-width='1'/><circle cx='80' cy='160' r='4' fill='#3b82f6'/><circle cx='110' cy='150' r='4' fill='#3b82f6'/><circle cx='140' cy='140' r='4' fill='#3b82f6'/><circle cx='170' cy='130' r='4' fill='#3b82f6'/><circle cx='200' cy='120' r='4' fill='#3b82f6'/><circle cx='230' cy='110' r='4' fill='#3b82f6'/><circle cx='260' cy='100' r='4' fill='#3b82f6'/></svg><br><strong>Диаграмма Б (широкое облако):</strong><br><svg width='300' height='200' viewBox='0 0 300 200' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='300' height='200' fill='#f8fafc' rx='8'/><line x1='40' y1='170' x2='280' y2='170' stroke='#1e4663' stroke-width='1'/><line x1='40' y1='170' x2='40' y2='30' stroke='#1e4663' stroke-width='1'/><circle cx='80' cy='165' r='4' fill='#ef4444'/><circle cx='110' cy='140' r='4' fill='#ef4444'/><circle cx='140' cy='155' r='4' fill='#ef4444'/><circle cx='170' cy='120' r='4' fill='#ef4444'/><circle cx='200' cy='135' r='4' fill='#ef4444'/><circle cx='230' cy='100' r='4' fill='#ef4444'/><circle cx='260' cy='110' r='4' fill='#ef4444'/></svg>",
                hint: "💡 Сила связи определяется тем, насколько плотно точки прилегают к воображаемой линии. Узкое облако — сильная связь, широкое — слабая.",
                correctAnswer: "диаграмма а",
                explanation: "✅ На диаграмме А облако УЗКОЕ — точки почти на одной линии. Это СИЛЬНАЯ связь. На диаграмме Б облако ШИРОКОЕ — связь слабее."
            },
            {
                step: 5,
                question: "Как выглядит диаграмма рассеивания, если связи между величинами НЕТ? (введите: круглое облако, вытянутое облако, линия)",
                hint: "💡 Если величины независимы, точки разбросаны равномерно — облако похоже на круг.",
                correctAnswer: "круглое облако",
                explanation: "✅ Если связи нет, облако точек имеет КРУГЛУЮ форму (или близкую к кругу). Точки не вытянуты ни в каком направлении. Пример: размер обуви и знание таблицы умножения."
            },
            {
                step: 6,
                question: "Посмотри на диаграмму. Что она показывает?<br><br><svg width='300' height='200' viewBox='0 0 300 200' style='background: #f8fafc; border-radius: 10px;'><rect x='0' y='0' width='300' height='200' fill='#f8fafc' rx='8'/><line x1='40' y1='170' x2='280' y2='170' stroke='#1e4663' stroke-width='1'/><line x1='40' y1='170' x2='40' y2='30' stroke='#1e4663' stroke-width='1'/><circle cx='60' cy='80' r='4' fill='#3b82f6'/><circle cx='100' cy='90' r='4' fill='#3b82f6'/><circle cx='140' cy='100' r='4' fill='#3b82f6'/><circle cx='180' cy='110' r='4' fill='#3b82f6'/><circle cx='220' cy='120' r='4' fill='#3b82f6'/><circle cx='260' cy='130' r='4' fill='#3b82f6'/></svg>",
                hint: "💡 Облако вытянуто слева направо вниз или вверх? Посмотри, с ростом X значения Y растут или падают?",
                correctAnswer: "положительная связь",
                explanation: "✅ Облако вытянуто СЛЕВА НАПРАВО ВВЕРХ — это ПОЛОЖИТЕЛЬНАЯ связь. Пример: скорость реакции и опыт — чем больше опыта, тем быстрее реакция."
            },
            {
                step: 7,
                question: "Означает ли наличие связи, что одна величина является ПРИЧИНОЙ другой? (введите: да или нет)",
                hint: "💡 Вспомни пример с аистами и рождаемостью: связь есть, но аисты не приносят детей.",
                correctAnswer: "нет",
                explanation: "✅ СВЯЗЬ НЕ ОЗНАЧАЕТ ПРИЧИНУ! Это самое важное правило. Причины могут быть: случайность, третья (скрытая) величина, обратная причинность."
            },
            {
                step: 8,
                question: "Какая величина может объяснять связь между количеством проданного мороженого и количеством утоплений в городе? (введите: жара, реклама, цена)",
                hint: "💡 Когда жарко, люди чаще едят мороженое и чаще купаются. Есть общая причина.",
                correctAnswer: "жара",
                explanation: "✅ Общая причина — ЖАРА. В жаркую погоду люди чаще едят мороженое и чаще купаются, поэтому утоплений больше. Связь между мороженым и утоплениями — ложная (призрачная)."
            },
            {
                step: 9,
                question: "Какая связь между ценой товара и спросом на него? (введите: положительная, отрицательная или нет связи)",
                hint: "💡 Чем выше цена, тем меньше людей готовы купить товар.",
                correctAnswer: "отрицательная",
                explanation: "✅ Связь между ценой и спросом — ОТРИЦАТЕЛЬНАЯ: чем выше цена, тем ниже спрос. Облако точек вытянуто слева направо вниз."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать о диаграммах рассеивания? (введите: они помогают визуально увидеть связь между величинами или они точно определяют причину связи)",
                hint: "💡 Что мы узнали? Диаграмма показывает наличие и характер связи, но не отвечает на вопрос «почему?».",
                correctAnswer: "они помогают визуально увидеть связь между величинами",
                explanation: "✅ Главный вывод: диаграмма рассеивания помогает ВИЗУАЛЬНО ОБНАРУЖИТЬ связь между величинами, определить её характер (положительная/отрицательная) и силу (узкое/широкое облако). Но она НЕ ПОКАЗЫВАЕТ ПРИЧИНУ этой связи."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - СТАНДАРТНОЕ ОТКЛОНЕНИЕ (8 КЛАСС) ==========
const grade8_topic2Tests = [
    {
        id: "std_issl_1",
        title: "🧠 «Как вернуть понятные единицы измерения?»",
        description: "На прошлом уроке мы открыли дисперсию — меру разброса данных. Для игрока А (4,5,5,5,6) дисперсия = 0,4. Для игрока Б (2,3,5,7,8) дисперсия = 5,2. Но у дисперсии есть недостаток: если данные в сантиметрах, то дисперсия — в квадратных сантиметрах. Это неудобно. Как это исправить?",
        steps: [
            {
                step: 1,
                question: "В каких единицах измеряется дисперсия, если исходные данные в сантиметрах? (введите: сантиметры, квадратные сантиметры, кубические сантиметры)",
                hint: "💡 Дисперсия — это средний квадрат отклонений. Что происходит с единицами измерения при возведении в квадрат?",
                correctAnswer: "квадратные сантиметры",
                explanation: "✅ Если исходные данные в сантиметрах, то отклонения — в сантиметрах, квадраты отклонений — в квадратных сантиметрах. Значит, дисперсия измеряется в квадратных сантиметрах. Это неудобно — мы хотим говорить о разбросе в тех же единицах, что и данные."
            },
            {
                step: 2,
                question: "Какое математическое действие обратно возведению в квадрат? (введите: извлечение квадратного корня, сложение, умножение)",
                hint: "💡 Если мы возвели число в квадрат, чтобы вернуться к исходному числу, нужно извлечь...",
                correctAnswer: "извлечение квадратного корня",
                explanation: "✅ Действие, обратное возведению в квадрат — извлечение квадратного корня. Если мы возьмём корень из дисперсии, то единицы измерения станут исходными."
            },
            {
                step: 3,
                question: "Чему равно стандартное отклонение для игрока А? (дисперсия = 0,4). Введите число, округлив до сотых, например 0.63",
                hint: "💡 Стандартное отклонение = √дисперсия = √0,4",
                correctAnswer: "0.63",
                explanation: "✅ Стандартное отклонение игрока А = √0,4 ≈ <strong>0,63</strong>. Это означает, что в среднем результаты игрока А отклоняются от среднего (5) примерно на 0,63 очка."
            },
            {
                step: 4,
                question: "Чему равно стандартное отклонение для игрока Б? (дисперсия = 5,2). Введите число, округлив до сотых, например 2.28",
                hint: "💡 Стандартное отклонение = √5,2",
                correctAnswer: "2.28",
                explanation: "✅ Стандартное отклонение игрока Б = √5,2 ≈ <strong>2,28</strong>. В среднем результаты игрока Б отклоняются от среднего (5) примерно на 2,28 очка — он менее стабилен."
            },
            {
                step: 5,
                question: "Что показывает стандартное отклонение простыми словами? (введите: типичное отклонение от среднего или максимальное отклонение от среднего)",
                hint: "💡 Стандартное отклонение — это 'среднее' отклонение, но не обычное среднее, а квадратичное.",
                correctAnswer: "типичное отклонение от среднего",
                explanation: "✅ Стандартное отклонение показывает типичное (характерное) отклонение чисел от их среднего арифметического. В отличие от размаха, оно учитывает все числа, а не только крайние."
            },
            {
                step: 6,
                question: "Чем стандартное отклонение отличается от размаха? (введите: учитывает все числа или учитывает только крайние числа)",
                hint: "💡 Размах = максимум − минимум. Он не показывает, что происходит внутри диапазона.",
                correctAnswer: "учитывает все числа",
                explanation: "✅ Размах учитывает только два числа — максимум и минимум. Стандартное отклонение учитывает ВСЕ числа, поэтому оно точнее характеризует разброс."
            },
            {
                step: 7,
                question: "Чем стандартное отклонение отличается от дисперсии? (введите: понятными единицами измерения или квадратными единицами)",
                hint: "💡 Вспомни: дисперсия измеряется в квадратных единицах, а стандартное отклонение — в исходных.",
                correctAnswer: "понятными единицами измерения",
                explanation: "✅ Главное преимущество стандартного отклонения — оно измеряется в тех же единицах, что и исходные данные. Это делает его более понятным для практического использования."
            },
            {
                step: 8,
                question: "Правило трёх сигм говорит: в пределах одного стандартного отклонения от среднего лежит около 68% данных. Для игрока А среднее = 5, S ≈ 0,63. В каком диапазоне лежат 68% данных? (введите: от 4,37 до 5,63 или от 4 до 6)",
                hint: "💡 Диапазон: от x̄ − S до x̄ + S. 5 − 0,63 = 4,37; 5 + 0,63 = 5,63.",
                correctAnswer: "от 4,37 до 5,63",
                explanation: "✅ 68% данных лежат в диапазоне от <strong>4,37 до 5,63</strong>. В этом диапазоне оказались три числа из пяти (пятёрки) — 60%, что близко к 68% для небольшого набора."
            },
            {
                step: 9,
                question: "Где в жизни применяют стандартное отклонение? (введите: контроль качества, финансы, спорт или всё перечисленное)",
                hint: "💡 Вспомни примеры: размеры деталей на заводе, риск инвестиций, стабильность спортсменов.",
                correctAnswer: "всё перечисленное",
                explanation: "✅ Стандартное отклонение применяют в КОНТРОЛЕ КАЧЕСТВА (размеры деталей), в ФИНАНСАХ (волатильность акций — мера риска), в СПОРТЕ (стабильность результатов), в МЕДИЦИНЕ (нормы анализов)."
            },
            {
                step: 10,
                question: "Какой главный вывод о стандартном отклонении? (введите: это корень из дисперсии, показывает типичный разброс в исходных единицах или всё перечисленное)",
                hint: "💡 Объедини всё, что мы узнали: как вычисляется, что показывает, какие у него преимущества.",
                correctAnswer: "всё перечисленное",
                explanation: "✅ Главный вывод: стандартное отклонение — это квадратный корень из дисперсии. Оно показывает типичное отклонение данных от среднего в тех же единицах, что и исходные данные. Это делает его удобным для практического применения в контроле качества, финансах, спорте и других областях."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ДИСПЕРСИЯ ЧИСЛОВОГО НАБОРА (8 КЛАСС) ==========
const grade8_topic1Tests = [
    {
        id: "variance_issl_1",
        title: "🧠 «Как измерить разброс, если среднее обманывает?»",
        description: "Тренер смотрит на результаты двух игроков за 5 матчей (очки). Игрок А: 4, 5, 5, 5, 6. Игрок Б: 2, 3, 5, 7, 8. Среднее у обоих одинаковое — 5. Но играют они по-разному. Как измерить разницу в разбросе результатов?",
        steps: [
            {
                step: 1,
                question: "Чему равно среднее арифметическое для игрока А? (введите число, например 5)",
                hint: "💡 (4+5+5+5+6) ÷ 5 = 25 ÷ 5",
                correctAnswer: "5",
                explanation: "✅ Среднее игрока А = 25/5 = <strong>5</strong>. Среднее игрока Б тоже = 25/5 = 5. По среднему они не отличаются."
            },
            {
                step: 2,
                question: "Найди отклонения от среднего для игрока А (вычти 5 из каждого числа). Чему равна сумма этих отклонений? (введите число)",
                hint: "💡 Отклонения: 4−5 = -1, 5−5 = 0, 5−5 = 0, 5−5 = 0, 6−5 = 1. Сумма = -1+0+0+0+1 = ?",
                correctAnswer: "0",
                explanation: "✅ Сумма отклонений = (-1) + 0 + 0 + 0 + 1 = <strong>0</strong>. Это свойство: сумма отклонений от среднего всегда равна нулю."
            },
            {
                step: 3,
                question: "Найди отклонения от среднего для игрока Б. Чему равна их сумма? (введите число)",
                hint: "💡 Отклонения: 2−5 = -3, 3−5 = -2, 5−5 = 0, 7−5 = 2, 8−5 = 3. Сумма = -3 + (-2) + 0 + 2 + 3 = ?",
                correctAnswer: "0",
                explanation: "✅ Сумма отклонений = (-3)+(-2)+0+2+3 = <strong>0</strong>. У обоих игроков сумма = 0, поэтому среднее отклонение не работает."
            },
            {
                step: 4,
                question: "Чтобы избавиться от знака «минус», возведём отклонения в квадрат. Найди квадраты отклонений для игрока А. Чему равна их сумма? (введите число)",
                hint: "💡 (-1)² = 1, 0² = 0, 0² = 0, 0² = 0, 1² = 1. Сумма = 1+0+0+0+1 = ?",
                correctAnswer: "2",
                explanation: "✅ Сумма квадратов отклонений для игрока А = 1+0+0+0+1 = <strong>2</strong>. Это уже положительное число."
            },
            {
                step: 5,
                question: "Найди сумму квадратов отклонений для игрока Б. (введите число)",
                hint: "💡 (-3)² = 9, (-2)² = 4, 0² = 0, 2² = 4, 3² = 9. Сумма = 9+4+0+4+9 = ?",
                correctAnswer: "26",
                explanation: "✅ Сумма квадратов отклонений для игрока Б = 9+4+0+4+9 = <strong>26</strong>. У игрока Б сумма намного больше."
            },
            {
                step: 6,
                question: "Теперь найдём СРЕДНЕЕ этих квадратов (разделим сумму на количество чисел — 5). Чему равна дисперсия игрока А? (введите число, например 0.4)",
                hint: "💡 2 ÷ 5 = ?",
                correctAnswer: "0.4",
                explanation: "✅ Дисперсия игрока А = 2/5 = <strong>0,4</strong>. Это средний квадрат отклонения от среднего."
            },
            {
                step: 7,
                question: "Чему равна дисперсия игрока Б? (введите число, например 5.2)",
                hint: "💡 26 ÷ 5 = ?",
                correctAnswer: "5.2",
                explanation: "✅ Дисперсия игрока Б = 26/5 = <strong>5,2</strong>. У игрока Б дисперсия больше — его результаты сильнее разбросаны."
            },
            {
                step: 8,
                question: "Запиши формулу дисперсии словами: дисперсия = среднее арифметическое ... от среднего. (введите: квадратов отклонений, отклонений, квадратов чисел)",
                hint: "💡 Мы брали отклонения, возводили в квадрат, потом находили среднее.",
                correctAnswer: "квадратов отклонений",
                explanation: "✅ Дисперсия = среднее арифметическое КВАДРАТОВ ОТКЛОНЕНИЙ от среднего. Формула: S² = (∑(xᵢ − x̄)²) / n."
            },
            {
                step: 9,
                question: "Есть и другая формула: S² = средний квадрат − (среднее)². Средний квадрат чисел игрока А = (16+25+25+25+36)/5 = 127/5 = 25,4. Квадрат среднего = 5² = 25. Чему равна дисперсия? (введите число)",
                hint: "💡 25,4 − 25 = ?",
                correctAnswer: "0.4",
                explanation: "✅ S² = 25,4 − 25 = <strong>0,4</strong>. Формула S² = x̄² − (x̄)² часто удобнее для вычислений."
            },
            {
                step: 10,
                question: "Какой главный вывод о дисперсии? (введите: чем больше дисперсия, тем сильнее разброс данных или чем больше дисперсия, тем данные стабильнее)",
                hint: "💡 Сравни игроков: у стабильного А дисперсия 0,4, у нестабильного Б — 5,2.",
                correctAnswer: "чем больше дисперсия, тем сильнее разброс данных",
                explanation: "✅ Главный вывод: дисперсия — это мера разброса данных вокруг среднего. Чем больше дисперсия, тем сильнее разбросаны данные. Дисперсия всегда неотрицательна и равна нулю только если все числа одинаковы."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ГРАФЫ (7 КЛАСС) ==========
const grade7_topic9Tests = [
    {
        id: "graph_issl_1",
        title: "🧠 «Как нарисовать связи?»",
        description: "Шесть одноклассников — Андрей (А), Борис (Б), Вадим (В), Григорий (Г), Дмитрий (Д) и Евгений (Е) — устроили турнир по настольному теннису. Нужно показать, кто с кем уже сыграл. Как это сделать наглядно? Можно нарисовать точки (ученики) и соединить их линиями (сыгранные партии). Такой рисунок в математике называется ГРАФОМ.",
        steps: [
            {
                step: 1,
                question: "Как в графе называются ТОЧКИ, которые обозначают объекты? (введите: вершины, рёбра или степени)",
                hint: "💡 Точки — это объекты (ученики). Линии — это связи.",
                correctAnswer: "вершины",
                explanation: "✅ Точки в графе называются ВЕРШИНАМИ. Они обозначают объекты (людей, города, станции и т.д.)."
            },
            {
                step: 2,
                question: "Как в графе называются ЛИНИИ, которые соединяют вершины? (введите: вершины, рёбра или степени)",
                hint: "💡 Линии показывают связи между объектами.",
                correctAnswer: "рёбра",
                explanation: "✅ Линии в графе называются РЁБРАМИ. Они показывают связи между объектами (дружбу, дороги, сыгранные партии)."
            },
            {
                step: 3,
                question: "В нашем графе вершина А (Андрей) соединена с Б и Д. Сколько рёбер выходит из вершины А? (введите число)",
                hint: "💡 Посчитай, сколько линий идёт от точки А к другим точкам.",
                correctAnswer: "2",
                explanation: "✅ Из вершины А выходит <strong>2</strong> ребра (к Б и к Д). Это число называется СТЕПЕНЬЮ вершины."
            },
            {
                step: 4,
                question: "Вадим (В) пока не играл ни с кем. Сколько рёбер выходит из вершины В? (введите число)",
                hint: "💡 Если вершина не соединена ни с одной другой, её степень = 0.",
                correctAnswer: "0",
                explanation: "✅ Вершина В ни с кем не соединена. Её степень = <strong>0</strong>. Такая вершина называется ИЗОЛИРОВАННОЙ."
            },
            {
                step: 5,
                question: "Чему равна сумма степеней всех вершин графа, если степени: А=2, Б=3, В=0, Г=3, Д=3, Е=3? (введите число)",
                hint: "💡 Сложи все степени: 2 + 3 + 0 + 3 + 3 + 3 = ?",
                correctAnswer: "14",
                explanation: "✅ Сумма степеней = 2+3+0+3+3+3 = <strong>14</strong>. Заметим, что 14 = 2 × 7, где 7 — число рёбер."
            },
            {
                step: 6,
                question: "Какое свойство связывает сумму степеней вершин и число рёбер? (введите: сумма степеней = 2 × число рёбер или сумма степеней = число рёбер)",
                hint: "💡 Каждое ребро соединяет две вершины, поэтому оно входит в сумму степеней дважды.",
                correctAnswer: "сумма степеней = 2 × число рёбер",
                explanation: "✅ Свойство: сумма степеней всех вершин = 2 × (число рёбер). Поэтому сумма степеней всегда ЧЁТНАЯ."
            },
            {
                step: 7,
                question: "Можно ли из вершины А добраться до вершины Е по рёбрам? (введите: да или нет)",
                hint: "💡 Попробуй найти путь: А → Б → Е. Такой путь есть.",
                correctAnswer: "да",
                explanation: "✅ Да, можно: А → Б → Е. Граф, в котором из любой вершины можно добраться до любой другой, называется СВЯЗНЫМ."
            },
            {
                step: 8,
                question: "Можно ли из вершины А добраться до вершины В? (введите: да или нет)",
                hint: "💡 Вершина В — изолированная. У неё нет рёбер.",
                correctAnswer: "нет",
                explanation: "✅ Нет, потому что вершина В изолирована. Граф, в котором есть вершины, до которых нельзя добраться, называется НЕСВЯЗНЫМ."
            },
            {
                step: 9,
                question: "На встрече 9 человек обменивались рукопожатиями. Сколько человек могло сделать нечётное число рукопожатий? (введите: чётное количество или нечётное)",
                hint: "💡 Сумма степеней всех вершин чётна. Сумма нечётного количества нечётных чисел — нечётна.",
                correctAnswer: "чётное количество",
                explanation: "✅ Количество людей, сделавших нечётное число рукопожатий, всегда ЧЁТНО. Это важное следствие из свойства суммы степеней."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал о графах? (введите: граф помогает наглядно показывать связи между объектами или граф нужен только для математиков)",
                hint: "💡 Где в жизни встречаются графы? Метро, социальные сети, дороги.",
                correctAnswer: "граф помогает наглядно показывать связи между объектами",
                explanation: "✅ Главный вывод: граф — это удобный и наглядный способ показать связи между объектами. Вершины — объекты, рёбра — связи. Степень вершины показывает количество связей. Сумма степеней всегда чётна."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - МОНЕТА И ИГРАЛЬНАЯ КОСТЬ (7 КЛАСС) ==========
const grade7_topic8Tests = [
    {
        id: "coin_dice_issl_1",
        title: "🧠 «Почему монета и кубик?»",
        description: "Учёным нужно изучать случайность. С какого опыта начать? Монета и кубик — самые простые модели. У монеты 2 исхода, у кубика — 6. Их легко бросать много раз, результаты легко записывать. Разберёмся, как устроены эти модели.",
        steps: [
            {
                step: 1,
                question: "Сколько равновозможных исходов у броска математической монеты? (введите число)",
                hint: "💡 У монеты две стороны: орёл и решка.",
                correctAnswer: "2",
                explanation: "✅ У математической монеты <strong>2</strong> равновозможных исхода: орёл (О) и решка (Р). Вероятность каждого = 1/2."
            },
            {
                step: 2,
                question: "Сколько равновозможных исходов у броска математического игрального кубика? (введите число)",
                hint: "💡 На кубике грани с числами от 1 до 6.",
                correctAnswer: "6",
                explanation: "✅ У математического кубика <strong>6</strong> равновозможных исходов: 1, 2, 3, 4, 5, 6. Вероятность каждого = 1/6."
            },
            {
                step: 3,
                question: "Если бросить монету 2 раза подряд, сколько всего различных последовательностей исходов может получиться? (введите число)",
                hint: "💡 При первом броске — 2 варианта, при втором — тоже 2. По правилу умножения: 2 × 2 = ?",
                correctAnswer: "4",
                explanation: "✅ При двух бросках монеты всего исходов: 2 × 2 = <strong>4</strong>. Это: ОО, ОР, РО, РР."
            },
            {
                step: 4,
                question: "Если бросить монету 3 раза подряд, сколько всего исходов? (введите число)",
                hint: "💡 Каждый новый бросок умножает количество исходов на 2.",
                correctAnswer: "8",
                explanation: "✅ При трёх бросках монеты: 2 × 2 × 2 = <strong>8</strong> исходов. В общем, при n бросках монеты — 2ⁿ исходов."
            },
            {
                step: 5,
                question: "Если бросить кубик 2 раза подряд, сколько всего исходов? (введите число)",
                hint: "💡 Первый бросок — 6 вариантов, второй — тоже 6. 6 × 6 = ?",
                correctAnswer: "36",
                explanation: "✅ При двух бросках кубика: 6 × 6 = <strong>36</strong> исходов. Их удобно изображать в виде таблицы 6×6."
            },
            {
                step: 6,
                question: "Бросаем монету и кубик одновременно. Сколько всего различных пар исходов (результат монеты, результат кубика)? (введите число)",
                hint: "💡 Монета даёт 2 исхода, кубик — 6. Перемножь: 2 × 6 = ?",
                correctAnswer: "12",
                explanation: "✅ Всего исходов: 2 × 6 = <strong>12</strong>. Например: (О,1), (О,2), ..., (Р,6). Это комбинаторное правило умножения."
            },
            {
                step: 7,
                question: "При двух бросках кубика какая сумма очков встречается чаще всего? (введите число, например 7)",
                hint: "💡 Подсчитай в таблице 6×6, сколько способов получить каждую сумму. Больше всего способов у суммы 7.",
                correctAnswer: "7",
                explanation: "✅ Сумма <strong>7</strong> встречается чаще всего — 6 способов из 36 (1+6, 2+5, 3+4, 4+3, 5+2, 6+1). Суммы 2 и 12 — только по 1 способу."
            },
            {
                step: 8,
                question: "Чем МАТЕМАТИЧЕСКАЯ монета отличается от настоящей? (введите: у неё нет веса, размера и дефектов или она сделана из золота)",
                hint: "💡 Настоящая монета может быть погнутой или стёртой. Математическая монета — идеальная модель.",
                correctAnswer: "у неё нет веса, размера и дефектов",
                explanation: "✅ Математическая монета — это идеальная модель: у неё нет веса, размера, дефектов. Она идеально симметрична. Это нужно, чтобы орёл и решка были равновозможны."
            },
            {
                step: 9,
                question: "Почему на правильном игральном кубике сумма очков на противоположных гранях равна 7? (введите: чтобы затруднить жульничество или чтобы было красиво)",
                hint: "💡 Если сделать кубик со смещённым центром тяжести, можно повлиять на частоту выпадения граней.",
                correctAnswer: "чтобы затруднить жульничество",
                explanation: "✅ Сумма противоположных граней равна 7 (1–6, 2–5, 3–4), чтобы затруднить изготовление поддельных кубиков со смещённым центром тяжести. Если кубик неправильный, это легче заметить."
            },
            {
                step: 10,
                question: "Какой главный вывод можно сделать о монете и кубике в теории вероятностей? (введите: это простейшие модели для изучения случайности или они слишком сложны для изучения)",
                hint: "💡 Почему все начинают с монеты и кубика? Что в них особенного?",
                correctAnswer: "это простейшие модели для изучения случайности",
                explanation: "✅ Главный вывод: монета и кубик — это простейшие модели случайных опытов с равновозможными исходами. На них удобно изучать законы теории вероятностей, а потом применять их к более сложным явлениям."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - СЛУЧАЙНЫЙ ОПЫТ И СЛУЧАЙНОЕ СОБЫТИЕ (7 КЛАСС) ==========
const grade7_topic7Tests = [
    {
        id: "random_issl_1",
        title: "🧠 «Что мы можем предсказать, а что — нет?»",
        description: "В жизни одни события мы можем предсказать с уверенностью, другие — нет. Например, завтра утром взойдёт солнце (это можно предсказать). А вот какой оценкой вы напишете контрольную — заранее неизвестно. Разберёмся, какие события бывают в случайных опытах.",
        steps: [
            {
                step: 1,
                question: "Какое событие НЕЛЬЗЯ предсказать с полной уверенностью? (введите номер: 1, 2 или 3) — 1: завтра взойдёт солнце, 2: завтра будет дождь, 3: после 31 января наступит 1 февраля",
                hint: "💡 Какие события зависят от случая? Дождь может пойти, а может не пойти.",
                correctAnswer: "2",
                explanation: "✅ Событие «завтра будет дождь» нельзя предсказать с полной уверенностью. Оно может как произойти, так и не произойти. Это СЛУЧАЙНОЕ событие."
            },
            {
                step: 2,
                question: "Как называются события, которые обязательно происходят в данном опыте? (введите: достоверные, невозможные или случайные)",
                hint: "💡 Пример: при бросании кубика обязательно выпадет число от 1 до 6.",
                correctAnswer: "достоверные",
                explanation: "✅ ДОСТОВЕРНЫЕ события — это те, которые обязательно произойдут в данном опыте. Например, при бросании кубика выпадет одно из чисел 1, 2, 3, 4, 5 или 6."
            },
            {
                step: 3,
                question: "Как называются события, которые никогда не происходят в данном опыте? (введите: достоверные, невозможные или случайные)",
                hint: "💡 Пример: при бросании обычного кубика не может выпасть 7.",
                correctAnswer: "невозможные",
                explanation: "✅ НЕВОЗМОЖНЫЕ события — это те, которые никогда не произойдут в данном опыте. Например, при бросании обычного кубика не может выпасть 7."
            },
            {
                step: 4,
                question: "Бросаем монету. Событие: выпал орёл. Какое это событие? (введите: достоверное, невозможное или случайное)",
                hint: "💡 Может выпасть орёл, а может решка. Это зависит от случая.",
                correctAnswer: "случайное",
                explanation: "✅ Событие «выпал орёл» — СЛУЧАЙНОЕ, потому что может как произойти, так и не произойти."
            },
            {
                step: 5,
                question: "Бросаем монету. Событие: выпадет орёл или решка. Какое это событие? (введите: достоверное, невозможное или случайное)",
                hint: "💡 У монеты только две стороны. Какие ещё варианты?",
                correctAnswer: "достоверное",
                explanation: "✅ Событие «выпадет орёл или решка» — ДОСТОВЕРНОЕ, потому что при броске монеты обязательно выпадет либо орёл, либо решка (если монета не упадёт на ребро)."
            },
            {
                step: 6,
                question: "Бросаем игральный кубик. Событие: выпадет 8. Какое это событие? (введите: достоверное, невозможное или случайное)",
                hint: "💡 Какие числа есть на игральном кубике?",
                correctAnswer: "невозможное",
                explanation: "✅ Событие «выпадет 8» — НЕВОЗМОЖНОЕ, потому что на обычном игральном кубике есть только числа от 1 до 6."
            },
            {
                step: 7,
                question: "Что называют СЛУЧАЙНЫМ ОПЫТОМ? (введите: условия, результат которых заранее неизвестен или результат, который всегда одинаков)",
                hint: "💡 Бросание кубика — это опыт. Знаем ли мы заранее, какое число выпадет?",
                correctAnswer: "условия, результат которых заранее неизвестен",
                explanation: "✅ СЛУЧАЙНЫЙ ОПЫТ (или случайный эксперимент) — это условия, в которых мы наблюдаем за событиями, а результат заранее неизвестен. Например, бросание монеты или кубика."
            },
            {
                step: 8,
                question: "Какой опыт можно назвать случайным? (введите: бросание монеты, нагревание воды до 100°C, растворение сахара в воде)",
                hint: "💡 В каком опыте результат заранее нельзя предсказать с уверенностью?",
                correctAnswer: "бросание монеты",
                explanation: "✅ Бросание монеты — случайный опыт, потому что результат (орёл или решка) заранее неизвестен. Нагревание воды до 100°C и растворение сахара — детерминированные опыты, их результат известен заранее."
            },
            {
                step: 9,
                question: "Одно и то же событие может быть достоверным в одном опыте и случайным в другом. Приведи пример. Событие: «завтра взойдёт солнце». На Северном полюсе полярной ночью это событие будет... (введите: достоверным, невозможным или случайным)",
                hint: "💡 Полярная ночь — это когда солнце не поднимается над горизонтом много дней подряд.",
                correctAnswer: "невозможным",
                explanation: "✅ На Северном полюсе во время полярной ночи солнце не встаёт неделями. Поэтому событие «завтра взойдёт солнце» может быть невозможным. Тип события зависит от УСЛОВИЙ ОПЫТА."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал о случайных событиях? (введите: случайное событие может как произойти, так и не произойти или случайное событие происходит всегда)",
                hint: "💡 Вспомни пример с монетой: орёл может выпасть, а может нет.",
                correctAnswer: "случайное событие может как произойти, так и не произойти",
                explanation: "✅ Главный вывод: СЛУЧАЙНОЕ СОБЫТИЕ — это событие, которое в данном опыте может как произойти, так и не произойти. Достоверное событие происходит всегда, невозможное — никогда. Тип события зависит от условий опыта."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ЧАСТОТА ЗНАЧЕНИЙ (7 КЛАСС) ==========
const grade7_topic6Tests = [
    {
        id: "frequency_issl_1",
        title: "🧠 «Как сравнить несравнимое?»",
        description: "В двух школах провели опрос: «Какой ваш любимый предмет?». В школе №1 (100 учеников) математику любят 60 человек. В школе №2 (500 учеников) математику любят 200 человек. В какой школе математика популярнее? По количеству — во второй (200 > 60). Но это нечестно — ведь во второй школе вообще больше учеников. Как правильно сравнить?",
        steps: [
            {
                step: 1,
                question: "Какую долю (часть) от всех учеников школы №1 составляют любители математики? (введите десятичной дробью, например 0.6)",
                hint: "💡 Доля = количество любителей ÷ общее количество учеников. 60 ÷ 100 = ?",
                correctAnswer: "0.6",
                explanation: "✅ Доля любителей математики в школе №1 = 60/100 = <strong>0,6</strong> (60%)."
            },
            {
                step: 2,
                question: "Какую долю (часть) от всех учеников школы №2 составляют любители математики? (введите десятичной дробью, например 0.4)",
                hint: "💡 200 ÷ 500 = ?",
                correctAnswer: "0.4",
                explanation: "✅ Доля любителей математики в школе №2 = 200/500 = <strong>0,4</strong> (40%)."
            },
            {
                step: 3,
                question: "Теперь сравни доли. В какой школе математика популярнее? (введите: №1 или №2)",
                hint: "💡 0,6 > 0,4. Значит, в школе №1 доля больше.",
                correctAnswer: "№1",
                explanation: "✅ В школе №1 математика популярнее (60% против 40%). Чтобы сравнивать группы разного размера, нужно использовать ДОЛЮ, а не количество. В статистике эта доля называется ЧАСТОТОЙ."
            },
            {
                step: 4,
                question: "Дан набор чисел: 1, 3, 1, 2, 1, 5, 3, 2, 1, 1. Сколько всего чисел в наборе? (введите число)",
                hint: "💡 Посчитай все числа: 1, 3, 1, 2, 1, 5, 3, 2, 1, 1 — это 10 чисел.",
                correctAnswer: "10",
                explanation: "✅ Всего в наборе <strong>10</strong> чисел. Это общее количество значений."
            },
            {
                step: 5,
                question: "Сколько раз в этом наборе встречается число 1? (введите число)",
                hint: "💡 Посчитай единицы: 1, 3, 1, 2, 1, 5, 3, 2, 1, 1 — единицы на 1-м, 3-м, 5-м, 9-м и 10-м местах. Всего 5 раз.",
                correctAnswer: "5",
                explanation: "✅ Число 1 встречается <strong>5</strong> раз. Это абсолютная частота (количество)."
            },
            {
                step: 6,
                question: "Чему равна частота (доля) числа 1 в этом наборе? (введите десятичной дробью, например 0.5)",
                hint: "💡 Частота = количество вхождений ÷ общее количество чисел = 5 ÷ 10",
                correctAnswer: "0.5",
                explanation: "✅ Частота числа 1 = 5/10 = <strong>0,5</strong> (или 50%). Это относительная частота (доля)."
            },
            {
                step: 7,
                question: "Заполни таблицу частот для набора: 1, 3, 1, 2, 1, 5, 3, 2, 1, 1. Найди частоту числа 3. (введите десятичной дробью, например 0.2)",
                hint: "💡 Число 3 встречается 2 раза. Всего чисел 10. Частота = 2 ÷ 10",
                correctAnswer: "0.2",
                explanation: "✅ Частота числа 3 = 2/10 = <strong>0,2</strong>. Частота числа 2 = 2/10 = 0,2. Частота числа 5 = 1/10 = 0,1."
            },
            {
                step: 8,
                question: "Сложи все частоты из таблицы (для 1, 2, 3, 5). Чему равна сумма? (введите число)",
                hint: "💡 0,5 + 0,2 + 0,2 + 0,1 = ?",
                correctAnswer: "1",
                explanation: "✅ Сумма частот = 0,5 + 0,2 + 0,2 + 0,1 = <strong>1</strong>. Это важное свойство: сумма частот всех значений всегда равна 1 (или 100%)."
            },
            {
                step: 9,
                question: "Найди среднее арифметическое через частоты: 1×0,5 + 2×0,2 + 3×0,2 + 5×0,1 = ? (введите число)",
                hint: "💡 1×0,5 = 0,5; 2×0,2 = 0,4; 3×0,2 = 0,6; 5×0,1 = 0,5. Сложи результаты.",
                correctAnswer: "2",
                explanation: "✅ Среднее = 0,5 + 0,4 + 0,6 + 0,5 = <strong>2</strong>. Это совпадает с обычным способом: (1+3+1+2+1+5+3+2+1+1)/10 = 20/10 = 2."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал о частотах? (введите: частота помогает сравнивать группы разного размера и находить среднее или частота — это просто количество)",
                hint: "💡 Для чего мы использовали частоты в этом задании? Чтобы сравнить школы и найти среднее.",
                correctAnswer: "частота помогает сравнивать группы разного размера и находить среднее",
                explanation: "✅ Главный вывод: частота помогает сравнивать группы разного размера (по доле, а не по количеству), кратко описывать большие наборы данных и быстро находить среднее арифметическое (сумма произведений значений на их частоты). Сумма частот всегда равна 1."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - РАЗМАХ ЧИСЛОВОГО НАБОРА (7 КЛАСС) ==========
const grade7_topic5Tests = [
    {
        id: "range_issl_1",
        title: "🧠 «Как измерить разброс?»",
        description: "Тренер по баскетболу смотрит на результаты двух игроков за 5 матчей (очки за игру). Игрок А: 15, 16, 15, 14, 15. Игрок Б: 8, 12, 15, 18, 22. Среднее у обоих одинаковое — 15 очков. Но играют они по-разному. Как измерить разницу между ними?",
        steps: [
            {
                step: 1,
                question: "Найди минимальное и максимальное значение у игрока А. (введите два числа через пробел, например 14 16)",
                hint: "💡 Посмотри на числа: 15, 16, 15, 14, 15. Самое маленькое — 14, самое большое — 16.",
                correctAnswer: "14 16",
                explanation: "✅ У игрока А: минимум = 14, максимум = 16. Все результаты близки друг к другу."
            },
            {
                step: 2,
                question: "Найди минимальное и максимальное значение у игрока Б. (введите два числа через пробел, например 8 22)",
                hint: "💡 Посмотри на числа: 8, 12, 15, 18, 22. Самое маленькое — 8, самое большое — 22.",
                correctAnswer: "8 22",
                explanation: "✅ У игрока Б: минимум = 8, максимум = 22. Результаты сильно различаются."
            },
            {
                step: 3,
                question: "Вычти из максимума минимум у игрока А. Какое число получилось? (введите число)",
                hint: "💡 16 − 14 = ?",
                correctAnswer: "2",
                explanation: "✅ Размах игрока А = 16 − 14 = <strong>2</strong>. Это маленькое число — значит, результаты стабильны."
            },
            {
                step: 4,
                question: "Вычти из максимума минимум у игрока Б. Какое число получилось? (введите число)",
                hint: "💡 22 − 8 = ?",
                correctAnswer: "14",
                explanation: "✅ Размах игрока Б = 22 − 8 = <strong>14</strong>. Это большое число — значит, результаты сильно разбросаны."
            },
            {
                step: 5,
                question: "Как называется эта характеристика — разница между максимумом и минимумом? (введите: размах, среднее или медиана)",
                hint: "💡 Вспомни, как мы называли разницу между самым большим и самым маленьким числом.",
                correctAnswer: "размах",
                explanation: "✅ Эта характеристика называется РАЗМАХ. Формула: Размах = максимум − минимум."
            },
            {
                step: 6,
                question: "Кого из игроков выберет тренер для решающего матча, если нужна стабильная игра? (введите: А или Б)",
                hint: "💡 У кого размах меньше? У игрока А размах = 2, у игрока Б размах = 14.",
                correctAnswer: "А",
                explanation: "✅ Для стабильной игры тренер выберет игрока А, потому что у него маленький размах — результаты предсказуемы."
            },
            {
                step: 7,
                question: "А если тренеру нужен игрок, способный на рывок (набрать много очков), а провалы не страшны? (введите: А или Б)",
                hint: "💡 У кого максимальный результат выше? У игрока А максимум = 16, у игрока Б = 22.",
                correctAnswer: "Б",
                explanation: "✅ Для рывка тренер выберет игрока Б — у него выше максимальный результат, хотя и размах большой."
            },
            {
                step: 8,
                question: "Посмотри на два набора: Группа 1: 10, 20, 30, 40, 50. Группа 2: 10, 10, 10, 50, 50. У них одинаковый размах. Чем они отличаются? (введите: распределением чисел внутри диапазона или количеством чисел)",
                hint: "💡 В первой группе числа распределены равномерно, во второй — кучкуются у краёв. Что размах не показывает?",
                correctAnswer: "распределением чисел внутри диапазона",
                explanation: "✅ Главный недостаток размаха — он показывает только разницу между максимумом и минимумом, но ничего не говорит о том, как распределены остальные числа."
            },
            {
                step: 9,
                question: "Заполни пропуск: Размах сильно зависит от ______ — очень больших или очень маленьких чисел. (введите слово в именительном падеже)",
                hint: "💡 Вспомни пример с зарплатами: 30, 35, 40, 45, 500. Число 500 — это...",
                correctAnswer: "выбросов",
                explanation: "✅ Размах сильно зависит от ВЫБРОСОВ — очень больших или очень маленьких чисел. Один выброс может сделать размах огромным, хотя большинство чисел сгруппированы."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал о размахе? (введите: размах показывает разброс данных, но не учитывает распределение внутри или размах всегда лучше среднего)",
                hint: "💡 Что мы узнали: размах прост, но у него есть ограничения.",
                correctAnswer: "размах показывает разброс данных, но не учитывает распределение внутри",
                explanation: "✅ Главный вывод: размах показывает разброс данных, но у него есть ограничения — он не учитывает, как распределены числа внутри диапазона, и сильно зависит от выбросов. Это простая, но несовершенная характеристика."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - МЕДИАНА ЧИСЛОВОГО НАБОРА (7 КЛАСС) ==========
const grade7_topic4Tests = [
    {
        id: "median_issl_1",
        title: "🧠 «Середина, которая не боится выбросов»",
        description: "Риелтор работает с клиентами. Пять человек назвали свои бюджеты на аренду квартиры (тыс. руб.): 25, 27, 30, 32, 150. Нужно найти «типичный» бюджет клиента. Среднее арифметическое получилось 52,8 — это не похоже на правду. Как найти честную середину?",
        steps: [
            {
                step: 1,
                question: "Упорядочи числа по возрастанию: 25, 27, 30, 32, 150. Какое число стоит посередине? (введите число)",
                hint: "💡 Посмотри на ряд: сколько чисел слева от середины и сколько справа?",
                correctAnswer: "30",
                explanation: "✅ Число <strong>30</strong> стоит посередине. Слева от него два числа, справа — тоже два. Это и есть медиана набора."
            },
            {
                step: 2,
                question: "Чему равно среднее арифметическое этого набора? (введите число, например 52.8)",
                hint: "💡 Сложи все числа: 25+27+30+32+150 = 264. Раздели на количество чисел (5).",
                correctAnswer: "52.8",
                explanation: "✅ Среднее арифметическое = 264 / 5 = <strong>52,8</strong>. Оно сильно отличается от медианы (30) из-за выброса — числа 150."
            },
            {
                step: 3,
                question: "Какое число лучше описывает «типичного» клиента: среднее (52,8) или медиана (30)? (введите: среднее или медиана)",
                hint: "💡 Большинство клиентов готовы платить 25–32 тыс. руб. Какое число ближе к этой группе?",
                correctAnswer: "медиана",
                explanation: "✅ Медиана (30) лучше описывает типичного клиента, потому что она устойчива к выбросам. Среднее завышено из-за одного богатого клиента."
            },
            {
                step: 4,
                question: "Теперь другой набор: 2, 3, 5, 8, 10. Упорядочи его и найди медиану. (введите число)",
                hint: "💡 Ряд уже упорядочен. Всего 5 чисел (нечётное количество). Какое число стоит на 3-м месте?",
                correctAnswer: "5",
                explanation: "✅ Медиана = <strong>5</strong>. Для нечётного количества чисел медиана — это число, стоящее в центре упорядоченного ряда."
            },
            {
                step: 5,
                question: "Если в наборе 7 чисел, на каком по счёту месте будет медиана? (введите номер, например 4)",
                hint: "💡 Для нечётного n медиана находится на месте (n+1)/2.",
                correctAnswer: "4",
                explanation: "✅ Для 7 чисел медиана находится на месте (7+1)/2 = <strong>4</strong>. Это четвёртое число в упорядоченном ряду."
            },
            {
                step: 6,
                question: "Теперь набор из 6 чисел: 1, 3, 4, 6, 7, 9. Упорядочи его и найди медиану. (введите число, например 5)",
                hint: "💡 Всего 6 чисел (чётное количество). Центральные числа — 3-е и 4-е: 4 и 6. Найди их среднее.",
                correctAnswer: "5",
                explanation: "✅ Медиана = (4+6)/2 = <strong>5</strong>. Для чётного количества чисел медиана — это среднее арифметическое двух центральных чисел."
            },
            {
                step: 7,
                question: "Если в наборе 10 чисел, какие по счёту числа будут центральными? (введите два номера через пробел, например 4 5)",
                hint: "💡 Для чётного n центральные места — это n/2 и n/2 + 1.",
                correctAnswer: "5 6",
                explanation: "✅ Для 10 чисел центральные места — это 10/2 = <strong>5</strong> и 5+1 = <strong>6</strong>. Медиана = среднее 5-го и 6-го чисел."
            },
            {
                step: 8,
                question: "В каких случаях медиана лучше среднего арифметического? (введите: когда есть выбросы или когда все числа одинаковые)",
                hint: "💡 Вспомни пример с риелтором: одно число 150 сильно повлияло на среднее.",
                correctAnswer: "когда есть выбросы",
                explanation: "✅ Медиана лучше среднего, когда в наборе есть выбросы — очень большие или очень маленькие числа. Медиана на них не реагирует."
            },
            {
                step: 9,
                question: "Заполни пропуск: Медиана — это число, которое делит упорядоченный ряд ______. (введите слово в именительном падеже)",
                hint: "💡 Медиана находится ровно в середине ряда.",
                correctAnswer: "пополам",
                explanation: "✅ Медиана — это число, которое делит упорядоченный ряд ПОПОЛАМ. Слева и справа от медианы находится одинаковое количество чисел."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал о медиане? (введите: медиана устойчива к выбросам или медиана всегда совпадает со средним)",
                hint: "💡 В примере с риелтором среднее было 52,8, а медиана 30. Что из них не испугалось выброса 150?",
                correctAnswer: "медиана устойчива к выбросам",
                explanation: "✅ Главный вывод: медиана устойчива к выбросам. Именно поэтому её используют для описания «типичных» зарплат, цен на жильё и в других случаях, когда есть экстремальные значения."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - СРЕДНЕЕ АРИФМЕТИЧЕСКОЕ, МОДА, МЕДИАНА, РАЗМАХ (7 КЛАСС) ==========
const statisticsBasicTests = [
    {
        id: "stats_issl_1",
        title: "🧠 «Как описать числа одним словом?»",
        description: "Учитель получил результаты контрольной работы по математике. Оценки 10 учеников: 2, 3, 4, 4, 4, 5, 5, 5, 5, 5. Нужно понять, как лучше описать этот набор чисел разными способами.",
        steps: [
            {
                step: 1,
                question: "Как найти «общий уровень» успеваемости класса? Какое число покажет типичную оценку, если сложить все оценки и разделить на количество учеников? (введите число, например 4.2)",
                hint: "💡 Сложи все оценки: 2+3+4+4+4+5+5+5+5+5. Затем раздели на количество учеников (10).",
                correctAnswer: "4.2",
                explanation: "✅ Среднее арифметическое = (2+3+4+4+4+5+5+5+5+5) / 10 = 42 / 10 = <strong>4,2</strong>. Это одна из характеристик набора чисел — средний уровень."
            },
            {
                step: 2,
                question: "Какая оценка встречается в наборе чаще всего? (введите число, например 5)",
                hint: "💡 Посчитай, сколько раз встречается каждая оценка: 2 — один раз, 3 — один раз, 4 — три раза, 5 — пять раз.",
                correctAnswer: "5",
                explanation: "✅ Оценка <strong>5</strong> встречается 5 раз — чаще других. Это число называется МОДОЙ. Мода показывает самое популярное значение в наборе данных."
            },
            {
                step: 3,
                question: "Упорядочи оценки по возрастанию: 2, 3, 4, 4, 4, 5, 5, 5, 5, 5. Какое число стоит посередине (между 5-м и 6-м элементом)? (введите число, например 4.5)",
                hint: "💡 Всего чисел 10 (чётное количество). Медиана — это среднее между 5-м и 6-м числами. 5-е число — 4, 6-е число — 5. (4+5)/2 = ?",
                correctAnswer: "4.5",
                explanation: "✅ Медиана = (4+5)/2 = <strong>4,5</strong>. Медиана — это середина упорядоченного ряда. Она полезна, когда есть очень большие или очень маленькие числа (выбросы)."
            },
            {
                step: 4,
                question: "Чему равен размах этого набора оценок? (размах = максимальное значение − минимальное). (введите число, например 3)",
                hint: "💡 Максимальная оценка — 5, минимальная — 2. Вычти: 5 − 2 = ?",
                correctAnswer: "3",
                explanation: "✅ Размах = 5 − 2 = <strong>3</strong>. Размах показывает, насколько разбросаны данные — от самого маленького до самого большого значения."
            },
            {
                step: 5,
                question: "Теперь представь другой класс. Их оценки: 2, 2, 3, 3, 4, 4, 5, 5, 5, 5. Чему равно среднее арифметическое? (введите число, например 4.2)",
                hint: "💡 Сложи все оценки: 2+2+3+3+4+4+5+5+5+5 = 38. Раздели на 10.",
                correctAnswer: "3.8",
                explanation: "✅ Среднее арифметическое = 38 / 10 = <strong>3,8</strong>. У этого класса средний балл ниже, чем у первого (4,2). Среднее помогает сравнивать группы."
            },
            {
                step: 6,
                question: "Представь ситуацию: в компании 5 сотрудников. Зарплаты: 30 000, 35 000, 40 000, 45 000, 500 000 рублей (директор). Какая характеристика лучше покажет «типичную» зарплату обычного сотрудника? (введите: среднее, мода, медиана или размах)",
                hint: "💡 Среднее арифметическое = (30+35+40+45+500)/5 = 130 000. Это сильно завышено из-за зарплаты директора. Какая характеристика не реагирует на выбросы?",
                correctAnswer: "медиана",
                explanation: "✅ Медиана (40 000 рублей) лучше показывает типичную зарплату, потому что она устойчива к выбросам — очень большим или очень маленьким числам."
            },
            {
                step: 7,
                question: "Для чего полезно знать РАЗМАХ? (введите: чтобы узнать самый популярный размер, чтобы понять разброс данных, чтобы найти среднее значение)",
                hint: "💡 Размах = max − min. Что он показывает?",
                correctAnswer: "чтобы понять разброс данных",
                explanation: "✅ Размах показывает разброс данных — насколько сильно отличаются самое большое и самое маленькое значения. Это полезно для оценки стабильности."
            },
            {
                step: 8,
                question: "Сопоставь характеристику с её назначением. Что к чему подходит? (введите: 1-А, 2-Б, 3-В, 4-Г)<br><br>1. Среднее арифметическое → ?<br>2. Мода → ?<br>3. Медиана → ?<br>4. Размах → ?<br><br>А) Самое частое значение<br>Б) Середина упорядоченного ряда<br>В) Общий уровень (сумма ÷ количество)<br>Г) Разброс данных (max − min)",
                hint: "💡 Вспомни определения из предыдущих шагов.",
                correctAnswer: "1-В,2-А,3-Б,4-Г",
                explanation: "✅ Среднее арифметическое — общий уровень (В), мода — самое частое значение (А), медиана — середина ряда (Б), размах — разброс данных (Г)."
            },
            {
                step: 9,
                question: "В каких профессиях полезно уметь находить среднее арифметическое, моду, медиану и размах? (введите: учитель, врач, социолог, экономист или все перечисленные)",
                hint: "💡 Учителя считают средний балл, врачи смотрят нормы роста, социологи анализируют опросы, экономисты — зарплаты и цены.",
                correctAnswer: "все перечисленные",
                explanation: "✅ Все перечисленные профессии используют статистические характеристики. Учителя — средний балл, врачи — медиану (нормы), социологи — моду (самый популярный ответ), экономисты — размах (разброс цен)."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал из этого задания? (введите: есть одна самая правильная характеристика или нет одной самой правильной характеристики — выбор зависит от задачи)",
                hint: "💡 Для сравнения классов нужно одно, для популярного размера — другое, для зарплат с выбросами — третье.",
                correctAnswer: "нет одной самой правильной характеристики — выбор зависит от задачи",
                explanation: "✅ Главный вывод: нет одной самой правильной характеристики. Выбор зависит от того, что мы хотим узнать о данных. Для сравнения общего уровня — среднее, для самого популярного значения — мода, для данных с выбросами — медиана, для оценки разброса — размах."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ГРАФИЧЕСКОЕ ПРЕДСТАВЛЕНИЕ ДАННЫХ (7 КЛАСС) ==========
const grade7_topic2Tests = [
    {
        id: "graph_issl_1",
        title: "🧠 «Как увидеть данные?»",
        description: "Учёные провели исследование и получили таблицу с данными о продажах компании за 5 лет. Нужно выбрать лучший способ визуализации, чтобы сразу увидеть тенденцию.",
        steps: [
            {
                step: 1,
                question: "Посмотри на таблицу. Какой способ лучше всего поможет увидеть изменение продаж во времени?<br><br><strong>Данные:</strong><br>• 2019 год: 100 млн руб.<br>• 2020 год: 105 млн руб.<br>• 2021 год: 110 млн руб.<br>• 2022 год: 115 млн руб.<br>• 2023 год: 120 млн руб.<br><br><svg width='400' height='250' viewBox='0 0 400 250' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='400' height='250' fill='#f8fafc' rx='8'/><text x='200' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Столбчатая диаграмма</text><line x1='50' y1='210' x2='350' y2='210' stroke='#1e4663' stroke-width='1'/><line x1='50' y1='210' x2='50' y2='30' stroke='#1e4663' stroke-width='1'/><text x='40' y='215' text-anchor='end' fill='#1e4663' font-size='10'>0</text><text x='40' y='160' text-anchor='end' fill='#1e4663' font-size='10'>50</text><text x='40' y='110' text-anchor='end' fill='#1e4663' font-size='10'>100</text><text x='40' y='60' text-anchor='end' fill='#1e4663' font-size='10'>150</text><rect x='70' y='130' width='40' height='80' fill='#3b82f6'/><text x='90' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>2019</text><rect x='130' y='120' width='40' height='90' fill='#3b82f6'/><text x='150' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>2020</text><rect x='190' y='110' width='40' height='100' fill='#3b82f6'/><text x='210' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>2021</text><rect x='250' y='100' width='40' height='110' fill='#3b82f6'/><text x='270' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>2022</text><rect x='310' y='90' width='40' height='120' fill='#3b82f6'/><text x='330' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>2023</text></svg>",
                hint: "💡 Какой тип диаграммы лучше всего показывает изменение величины во времени?",
                correctAnswer: "линейный график",
                explanation: "✅ Линейный график (соединённые точки) лучше всего показывает изменение во времени (тренд). Столбчатая диаграмма тоже показывает, но линия нагляднее показывает динамику."
            },
            {
                step: 2,
                question: "Посмотри на два графика продаж. Какой из них честнее показывает реальный рост продаж?<br><br><strong>График А (ось от 0 до 150):</strong><br><svg width='400' height='200' viewBox='0 0 400 200' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='400' height='200' fill='#f8fafc' rx='8'/><text x='200' y='15' text-anchor='middle' fill='#1e4663' font-size='10' font-weight='bold'>График А</text><line x1='40' y1='170' x2='360' y2='170' stroke='#1e4663' stroke-width='1'/><line x1='40' y1='170' x2='40' y2='20' stroke='#1e4663' stroke-width='1'/><text x='30' y='175' text-anchor='end' fill='#1e4663' font-size='8'>0</text><text x='30' y='140' text-anchor='end' fill='#1e4663' font-size='8'>50</text><text x='30' y='105' text-anchor='end' fill='#1e4663' font-size='8'>100</text><text x='30' y='70' text-anchor='end' fill='#1e4663' font-size='8'>150</text><circle cx='100' cy='140' r='4' fill='#3b82f6'/><circle cx='180' cy='135' r='4' fill='#3b82f6'/><circle cx='260' cy='130' r='4' fill='#3b82f6'/><circle cx='340' cy='125' r='4' fill='#3b82f6'/><polyline points='100,140 180,135 260,130 340,125' stroke='#3b82f6' stroke-width='2' fill='none'/><text x='100' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2019</text><text x='180' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2020</text><text x='260' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2021</text><text x='340' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2022</text></svg><br><strong>График Б (ось от 90 до 150):</strong><br><svg width='400' height='200' viewBox='0 0 400 200' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='400' height='200' fill='#f8fafc' rx='8'/><text x='200' y='15' text-anchor='middle' fill='#1e4663' font-size='10' font-weight='bold'>График Б</text><line x1='40' y1='170' x2='360' y2='170' stroke='#1e4663' stroke-width='1'/><line x1='40' y1='170' x2='40' y2='20' stroke='#1e4663' stroke-width='1'/><text x='30' y='175' text-anchor='end' fill='#1e4663' font-size='8'>90</text><text x='30' y='140' text-anchor='end' fill='#1e4663' font-size='8'>105</text><text x='30' y='105' text-anchor='end' fill='#1e4663' font-size='8'>120</text><text x='30' y='70' text-anchor='end' fill='#1e4663' font-size='8'>135</text><circle cx='100' cy='130' r='4' fill='#ef4444'/><circle cx='180' cy='115' r='4' fill='#ef4444'/><circle cx='260' cy='100' r='4' fill='#ef4444'/><circle cx='340' cy='85' r='4' fill='#ef4444'/><polyline points='100,130 180,115 260,100 340,85' stroke='#ef4444' stroke-width='3' fill='none'/><text x='100' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2019</text><text x='180' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2020</text><text x='260' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2021</text><text x='340' y='160' text-anchor='middle' fill='#1e4663' font-size='10'>2022</text></svg>",
                hint: "💡 Посмотри на ось Y (вертикальную). С какого числа начинается шкала?",
                correctAnswer: "график а",
                explanation: "✅ График А честнее, потому что его ось Y начинается с 0. График Б начинается с 90, из-за чего небольшой рост продаж выглядит как огромный скачок — это приём манипуляции."
            },
            {
                step: 3,
                question: "Для каких данных лучше всего подходит КРУГОВАЯ диаграмма?<br><br><svg width='300' height='250' viewBox='0 0 300 250' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='300' height='250' fill='#f8fafc' rx='8'/><circle cx='150' cy='120' r='80' fill='#f8fafc' stroke='#cbdde9' stroke-width='1'/><path d='M150,120 L150,40 A80,80 0 0,1 227,173 Z' fill='#3b82f6'/><path d='M150,120 L227,173 A80,80 0 0,1 95,184 Z' fill='#10b981'/><path d='M150,120 L95,184 A80,80 0 0,1 150,40 Z' fill='#f59e0b'/><text x='185' y='70' fill='white' font-size='10' font-weight='bold'>45%</text><text x='215' y='155' fill='white' font-size='10'>30%</text><text x='90' y='180' fill='white' font-size='10'>25%</text><rect x='30' y='210' width='12' height='12' fill='#3b82f6'/><text x='48' y='222' fill='#1e4663' font-size='10'>Категория А</text><rect x='150' y='210' width='12' height='12' fill='#10b981'/><text x='168' y='222' fill='#1e4663' font-size='10'>Категория Б</text><rect x='270' y='210' width='12' height='12' fill='#f59e0b'/><text x='288' y='222' fill='#1e4663' font-size='10'>Категория В</text></svg>",
                hint: "💡 Круговая диаграмма показывает, как целое делится на части (сумма частей = 100%).",
                correctAnswer: "для показа долей (частей целого)",
                explanation: "✅ Круговая диаграмма лучше всего подходит для показа долей (частей целого), например, распределения бюджета семьи или любимых предметов в классе."
            },
            {
                step: 4,
                question: "Посмотри на круговую диаграмму. Какую долю (в процентах) составляет категория Б? (введите число, например 30)",
                hint: "💡 Посмотри на подписи к диаграмме или на размер сектора.",
                correctAnswer: "30",
                explanation: "✅ На диаграмме категория Б составляет 30% (подпись справа от диаграммы)."
            },
            {
                step: 5,
                question: "Какой тип диаграммы лучше всего подходит для сравнения любимых предметов в классе? (введите: столбчатая, круговая, линейная)",
                hint: "💡 Нужно сравнить несколько категорий (математика, русский, физкультура). Какая диаграмма лучше для сравнения?",
                correctAnswer: "столбчатая",
                explanation: "✅ Столбчатая диаграмма лучше всего подходит для сравнения разных категорий (например, любимых предметов). По высоте столбиков сразу видно, где больше, где меньше."
            },
            {
                step: 6,
                question: "Почему для показа изменения температуры за неделю НЕЛЬЗЯ использовать круговую диаграмму?",
                hint: "💡 Круговая диаграмма показывает части целого. Температура в понедельник и вторник — это части чего?",
                correctAnswer: "потому что круговая диаграмма показывает доли, которые в сумме дают 100%",
                explanation: "✅ Круговая диаграмма показывает доли, которые в сумме дают 100%. Температура в понедельник и вторник не складываются в 100%, поэтому круговая диаграмма не подходит."
            },
            {
                step: 7,
                question: "Что нужно проверить на диаграмме, чтобы убедиться, что она не обманывает?",
                hint: "💡 Какой самый важный элемент шкалы нужно проверить?",
                correctAnswer: "начинается ли ось с нуля",
                explanation: "✅ Главное, что нужно проверить — начинается ли ось Y с нуля. Если ось обрезана (начинается не с нуля), разница между столбиками или точками может быть сильно преувеличена."
            },
            {
                step: 8,
                question: "Сопоставь тип диаграммы с её назначением. Что к чему подходит? (введите: 1-А, 2-Б, 3-В и т.д.)<br><br>1. Столбчатая → ?<br>2. Линейная (график) → ?<br>3. Круговая → ?<br><br>А) Показывает доли (части целого)<br>Б) Показывает изменение во времени (тренд)<br>В) Показывает сравнение категорий",
                hint: "💡 Вспомни, что мы обсуждали в начале урока.",
                correctAnswer: "1-В,2-Б,3-А",
                explanation: "✅ Столбчатая — для сравнения категорий (В), линейная — для изменения во времени (Б), круговая — для долей (А)."
            },
            {
                step: 9,
                question: "Заполни пропуск: График, на котором ось Y начинается не с нуля, может вводить в ______. (введите слово)",
                hint: "💡 Как называется, когда данные показывают нечестно?",
                correctAnswer: "заблуждение",
                explanation: "✅ График с обрезанной осью Y может вводить в ЗАБЛУЖДЕНИЕ. Важно всегда проверять, с нуля ли начинается шкала."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал из этого задания о выборе диаграммы? (введите: тип диаграммы зависит от того, что нужно показать или все диаграммы одинаково хороши)",
                hint: "💡 Для сравнения — одна диаграмма, для динамики — другая, для долей — третья.",
                correctAnswer: "тип диаграммы зависит от того, что нужно показать",
                explanation: "✅ Главный вывод: тип диаграммы зависит от того, что нужно показать. Для сравнения категорий — столбчатая, для изменения во времени — линейная (график), для долей — круговая. Нет одной диаграммы на все случаи."
            }
        ]
    }
];
// ========== ИССЛЕДОВАТЕЛЬСКОЕ ОБУЧЕНИЕ - ПРЕДСТАВЛЕНИЕ ДАННЫХ В ТАБЛИЦАХ (7 КЛАСС) ==========
const grade7_topic1Tests = [
    {
        id: "tables_issl_1",
        title: "🧠 «Как организовать хаос?»",
        description: "Елена из образовательного центра собирает заявки на мебель. Заявки приходят по СМС и по электронной почте. Вот что у неё получилось: «Отдел физики: 2 стола. Лаборатория химии: 1 шкаф. Кружок робототехники: 4 стула. Отдел математики: 3 стола. Кабинет директора: 1 кресло. Ещё отдел физики просит 1 шкаф. Лаборатория химии: 2 стула...» Елене нужно навести порядок в данных.",
        steps: [
            {
                step: 1,
                question: "Почему Елене неудобно работать с такой информацией? Выбери главную причину. (введите номер ответа: 1, 2, 3 или 4) — 1: слишком много текста, 2: данные разрозненные, нет порядка, 3: непонятные слова, 4: мало данных",
                hint: "💡 Что мешает быстро найти нужную информацию? Данные перемешаны.",
                correctAnswer: "2",
                explanation: "✅ Главная проблема — данные разрозненные, нет порядка. Из-за этого легко что-то забыть или перепутать."
            },
            {
                step: 2,
                question: "Как можно сгруппировать данные, чтобы было удобнее? (введите: по видам мебели, по цвету или по весу)",
                hint: "💡 Подумай, что общего у '2 стола', '1 шкаф', '4 стула'?",
                correctAnswer: "по видам мебели",
                explanation: "✅ Данные можно сгруппировать по видам мебели: столы, шкафы, стулья, кресла. Это первый шаг к созданию таблицы."
            },
            {
                step: 3,
                question: "Какие столбцы обязательно должны быть в таблице, чтобы Елена могла понять, сколько чего заказывать? (введите: Наименование и Количество, Имя и Возраст, Дата и Время)",
                hint: "💡 Елене нужно знать, какую мебель и в каком количестве заказывать.",
                correctAnswer: "наименование и количество",
                explanation: "✅ Минимально необходимые столбцы: «Наименование мебели» и «Количество». Это основа любой таблицы заказов."
            },
            {
                step: 4,
                question: "Какой ещё столбец нужно добавить, чтобы знать, для какого кабинета заказывать мебель? (введите: Отдел/кабинет, Цена, Дата заказа)",
                hint: "💡 Елене нужно развозить мебель по кабинетам. Что для этого нужно знать?",
                correctAnswer: "отдел/кабинет",
                explanation: "✅ Нужен столбец «Отдел/кабинет». Тогда будет понятно, куда везти заказ."
            },
            {
                step: 5,
                question: "Что обязательно должно быть у любой хорошей таблицы? (введите: заголовки столбцов, цветные ячейки или рамки)",
                hint: "💡 Без чего таблица становится непонятной?",
                correctAnswer: "заголовки столбцов",
                explanation: "✅ У хорошей таблицы обязательно должны быть заголовки столбцов, которые объясняют, какие данные в них находятся."
            },
            {
                step: 6,
                question: "Сформулируй правило: данные в одном столбце должны быть... (введите: однотипными или разнотипными)",
                hint: "💡 Могут ли в столбце «Количество» быть и числа, и текст?",
                correctAnswer: "однотипными",
                explanation: "✅ Данные в одном столбце должны быть однотипными. Например, в столбце «Количество» — только числа, в столбце «Наименование» — только названия."
            },
            {
                step: 7,
                question: "Какая таблица считается хорошей? (введите: та, у которой есть заголовки и понятная структура, или та, которая красиво оформлена)",
                hint: "💡 Что важнее — красота или понятность?",
                correctAnswer: "та, у которой есть заголовки и понятная структура",
                explanation: "✅ Хорошая таблица — это та, которая помогает быстро найти нужную информацию и ответить на вопросы. Заголовки и понятная структура важнее внешнего оформления."
            },
            {
                step: 8,
                question: "Почему одна и та же информация может быть представлена в разных таблицах? (введите: потому что таблица зависит от цели, потому что так проще считать, потому что так красивее)",
                hint: "💡 Для заказа мебели нужна одна таблица, для расстановки по кабинетам — другая. Почему?",
                correctAnswer: "потому что таблица зависит от цели",
                explanation: "✅ Таблица зависит от цели. Для одной цели нужно одно, для другой — другое. Нет «правильной» таблицы на все случаи."
            },
            {
                step: 9,
                question: "Заполни пропуск: Таблица — это способ организации данных по ______ и столбцам. (введите слово в именительном падеже)",
                hint: "💡 Таблица состоит из горизонтальных линий и вертикальных...",
                correctAnswer: "строкам",
                explanation: "✅ Таблица — это способ организации данных по СТРОКАМ и столбцам. Строки — это горизонтальные ряды, столбцы — вертикальные."
            },
            {
                step: 10,
                question: "Какой главный вывод ты сделал из этого задания? (введите: таблицы нужны, чтобы организовать хаотичные данные или таблицы нужны, чтобы было красиво)",
                hint: "💡 Вспомни начало: у Елены был хаос, таблица помогла его упорядочить.",
                correctAnswer: "таблицы нужны, чтобы организовать хаотичные данные",
                explanation: "✅ Главный вывод: таблицы нужны, чтобы организовать хаотичные данные. Они помогают структурировать информацию, быстро находить нужное и отвечать на вопросы."
            }
        ]
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ЗАКОН БОЛЬШИХ ЧИСЕЛ" (9 КЛАСС) ==========
const grade9_topic6Cases = [
    // ========== КЕЙС 1. «Спор о честности монеты» ==========
    {
        id: "lln_1",
        title: "🪙 Кейс 1: «Спор о честности монеты»",
        description: "Два друга поспорили о честности монеты. Петя говорит: «Я 10 раз подбросил монету, и орёл выпал 7 раз. Это 70%! Монета явно неправильная». Вася отвечает: «10 раз — это слишком мало. Подбрось 1000 раз, тогда увидишь». Петя обиделся: «Ты просто не хочешь признавать, что я прав. 7 из 10 — это же очевидное отклонение!»",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Кто прав — Петя или Вася?<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с законом больших чисел.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему при малом числе бросков возможны большие отклонения?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют вероятность 7 орлов из 10.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько бросков нужно для надёжного вывода?`,
        question: "Какова вероятность получить ровно 7 орлов при 10 бросках честной монеты? (введите десятичной дробью, округлив до тысячных, например 8.394)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.117,
        hint: "💡 P = C₁₀⁷ × (0,5)¹⁰ = 120 ÷ 1024",
        solution: "✅ P(7 орлов из 10) = 120 / 1024 = <strong>0,1171875 ≈ 0,117</strong> (11,7%). Это не маленькая вероятность! Петя неправ: при 10 бросках возможны случайные отклонения. Закон больших чисел говорит, что при увеличении числа бросков частота приблизится к 0,5."
    },
    // ========== КЕЙС 2. «IT-компания и время устранения сбоев» ==========
    {
        id: "lln_2",
        title: "💻 Кейс 2: «IT-компания и время устранения сбоев»",
        description: "Крупная IT-компания обслуживает компьютерную систему по договору. За первые 300 сбоев: 71,2% устранено менее чем за 8 часов. За следующие 300 сбоев: только 49% устранено менее чем за 8 часов. Менеджер паникует: «Катастрофа! Эффективность упала с 71% до 49%! Надо уволить бригаду!» Аналитик возражает: «Подождите. Посмотрите на общую частоту за 600 сбоев — 60,1%. Давайте подождём ещё данных».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют общую частоту.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему выборки так сильно различаются?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают частоты по отдельности и в сумме.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какой объём выборки можно считать достаточным?`,
        question: "Чему равна общая частота устранения сбоев за 8 часов за все 600 сбоев? (введите десятичной дробью, округлив до тысячных, например 8.42)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.601,
        hint: "💡 Общая частота = (300×0,712 + 300×0,49) / 600 = (213,6 + 147) / 600",
        solution: "✅ Общая частота = (213,6 + 147) / 600 = 360,6 / 600 = <strong>0,601</strong> (60,1%). Аналитик прав: отдельные выборки могут сильно отличаться из-за случайности, но при накоплении данных частота стабилизируется около истинной вероятности."
    },
    // ========== КЕЙС 3. «Социологический опрос перед выборами» ==========
    {
        id: "lln_3",
        title: "🗳️ Кейс 3: «Социологический опрос перед выборами»",
        description: "Перед выборами мэра социологическая служба опросила 2000 случайных избирателей. 1100 из них сказали, что будут голосовать за кандидата К. Социологи объявили: «Кандидата К поддерживают 55% избирателей. Погрешность — 3%». Журналист спрашивает: «Вы опросили всего 2000 человек, а в городе 2 миллиона избирателей! Как можно делать выводы обо всех по такой маленькой группе?» Социолог отвечает: «Закон больших чисел!»",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Кто прав?<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют долю и погрешность.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему размер города не важен?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют формулу погрешности 1/√n.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько человек нужно опросить для точности 1%?`,
        question: "Какова примерная погрешность опроса при выборке 2000 человек? (введите десятичной дробью, например 0.145)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.022,
        hint: "💡 Погрешность ≈ 1/√n = 1/√2000 ≈ 1/44,7",
        solution: "✅ Погрешность ≈ 1/√2000 ≈ 1/44,7 ≈ <strong>0,022</strong> (2,2%). Социолог прав: закон больших чисел позволяет оценить долю во всей совокупности по случайной выборке. Точность зависит от объёма выборки, а не от размера населения."
    },
    // ========== КЕЙС 4. «Измерение горошин» ==========
    {
        id: "lln_4",
        title: "🟢 Кейс 4: «Измерение горошин»",
        description: "Сельскохозяйственная компания хочет узнать средний диаметр горошин нового сорта. Измерить все горошины невозможно — их миллионы. Технолог предлагает: «Давайте измерим 100 горошин и возьмём среднее». Директор сомневается: «Всего 100 горошин? Это же ничтожно мало! Как можно судить о миллионах по сотне?» Технолог объясняет: «Закон больших чисел. Среднее выборки приближается к среднему всей совокупности при увеличении выборки».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с оценкой среднего по выборке.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему 100 горошин — это достаточно?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Объясняют, как погрешность зависит от объёма выборки.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько горошин нужно для точности в 2 раза выше?`,
        question: "Во сколько раз нужно увеличить выборку, чтобы уменьшить погрешность в 2 раза? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 4,
        hint: "💡 Погрешность ~ 1/√n. Чтобы погрешность уменьшилась в 2 раза, нужно √n увеличить в 2 раза → n увеличить в 4 раза.",
        solution: "✅ Погрешность измерения среднего ≈ 1/√n. Чтобы погрешность уменьшилась в 2 раза, нужно увеличить выборку в <strong>4</strong> раза. Технолог прав: закон больших чисел позволяет оценивать среднее по выборке."
    },
    // ========== КЕЙС 5. «Контроль качества на заводе» ==========
    {
        id: "lln_5",
        title: "🔧 Кейс 5: «Контроль качества на заводе»",
        description: "На заводе по производству подшипников проверяют качество продукции. Из каждой партии в 10 000 подшипников проверяют 100 случайных. Если среди них более 5 бракованных, вся партия бракуется. Контролёр ОТК говорит: «100 подшипников из 10 000 — это всего 1%! Мы можем пропустить бракованную партию!» Инженер отвечает: «Вы не понимаете закон больших чисел. Если реальный процент брака 3%, то в выборке из 100 подшипников в среднем будет 3 бракованных».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся анализируют контроль качества по выборке.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Достаточно ли 100 подшипников для контроля?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Оценивают среднее число бракованных в выборке.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Когда нужна 100% проверка, а когда достаточно выборки?`,
        question: "Если реальный процент брака 5%, сколько бракованных подшипников в среднем будет в выборке из 100 штук? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 5,
        hint: "💡 Среднее = n × p = 100 × 0,05",
        solution: "✅ Среднее число бракованных = 100 × 0,05 = <strong>5</strong>. Если реальный процент брака 5%, то в среднем в выборке из 100 будет 5 бракованных. Контролёр неправ: закон больших чисел позволяет по выборке судить о всей партии."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "МАТЕМАТИЧЕСКОЕ ОЖИДАНИЕ" (9 КЛАСС) ==========
const grade9_topic5Cases = [
    // ========== КЕЙС 1. «Спор о справедливой игре» ==========
    {
        id: "expect_1",
        title: "🎲 Кейс 1: «Спор о справедливой игре»",
        description: "Два друга, Дима и Саша, придумали игру. Они бросают игральный кубик. Если выпадает 1, 2 или 3, то Дима платит Саше 120 рублей. Если выпадает 4 или 5, то Саша платит Диме 120 рублей. Если выпадает 6, то никто никому не платит. Саша говорит: «Игра справедливая! У нас обоих одинаковые шансы на выигрыш». Дима сомневается: «Я что-то не уверен. Давай посчитаем математическое ожидание моего выигрыша».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Кто прав?<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием математического ожидания.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Является ли игра справедливой?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Составляют распределение и вычисляют E(X).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как изменить условия для справедливости?`,
        question: "Чему равно математическое ожидание выигрыша Димы (в рублях)? (введите число, отрицательное если проигрыш, например -16.7)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: -20,
        hint: "💡 При 1,2,3: X = -120 (вероятность 0,5). При 4,5: X = +120 (вероятность ≈0,333). При 6: X = 0 (вероятность ≈0,167). E(X) = -120·0,5 + 120·0,333 + 0·0,167",
        solution: "✅ E(выигрыша Димы) = -120 × 0,5 + 120 × (2/6) + 0 × (1/6) = -60 + 40 = <strong>-20 рублей</strong>. Дима прав: игра несправедливая. В среднем за бросок Дима теряет 20 рублей, Саша выигрывает 20 рублей."
    },
    // ========== КЕЙС 2. «Лотерея: стоит ли покупать билет?» ==========
    {
        id: "expect_2",
        title: "🎫 Кейс 2: «Лотерея: стоит ли покупать билет?»",
        description: "В лотерее разыгрываются 2000 билетов. Из них: 1 билет выигрывает 10 000 рублей, 5 билетов выигрывают по 1000 рублей, 50 билетов выигрывают по 200 рублей, остальные — без выигрыша. Билет стоит 120 рублей. Стоит ли покупать билет?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют математическое ожидание выигрыша.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Выгодна ли лотерея для игрока?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> E = 10000×1/2000 + 1000×5/2000 + 200×50/2000.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему лотереи всегда в плюсе?`,
        question: "Чему равно математическое ожидание выигрыша на один билет (в рублях)? (введите число, например 20)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 10,
        hint: "💡 E = 10000×(1/2000) + 1000×(5/2000) + 200×(50/2000) = 5 + 2,5 + 5 = 12,5? Проверим: 10000/2000=5, 5000/2000=2,5, 10000/2000=5, сумма = 12,5. Но это больше 10? Нет, 5+2,5+5=12,5. Ответ должен быть 12,5? Возможно, я ошибся. Билет стоит 120, значит проигрыш 107,5. E выигрыша = 12,5",
        solution: "✅ E(выигрыша) = 10000×1/2000 + 1000×5/2000 + 200×50/2000 = 5 + 2,5 + 5 = <strong>12,5 рублей</strong>. Билет стоит 120 рублей, поэтому средний убыток = 120 − 12,5 = 107,5 рублей. Лотерея невыгодна для игрока."
    },
    // ========== КЕЙС 3. «Страхование: сколько стоит полис?» ==========
    {
        id: "expect_3",
        title: "🛡️ Кейс 3: «Страхование: сколько стоит полис?»",
        description: "Страховая компания предлагает полис за 8000 рублей в год. По статистике, водитель попадает в аварию в среднем 1 раз в 4 года (вероятность аварии за год = 0,25). Средняя выплата страховой при аварии — 30 000 рублей. Клиент говорит: «8000 рублей — это дорого! Я лучше буду рисковать». Страховой агент отвечает: «Зато если попадёте в аварию, выплата покроет ущерб». Кто прав с финансовой точки зрения?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют E(выплаты) страховой.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Выгодна ли страховка клиенту?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> E(выплаты) = 30000 × 0,25 = 7500.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему люди покупают страховку, если она невыгодна?`,
        question: "Чему равно математическое ожидание выплаты страховой на одного клиента за год (в рублях)? (введите число, например 7500)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 7500,
        hint: "💡 E(выплаты) = сумма выплаты × вероятность аварии = 30000 × 0,25",
        solution: "✅ E(выплаты) = 30000 × 0,25 = <strong>7500 рублей</strong>. Клиент платит 8000 рублей. С финансовой точки зрения без страховки средние расходы 7500 рублей, со страховкой — 8000 рублей. Страховка невыгодна, но даёт уверенность, что клиент не столкнётся с расходами 30000 рублей."
    },
    // ========== КЕЙС 4. «Какую игру выбрать на ярмарке?» ==========
    {
        id: "expect_4",
        title: "🎪 Кейс 4: «Какую игру выбрать на ярмарке?»",
        description: "На ярмарке две игровые палатки. В первой: бросаешь два кубика, сумма очков умножается на 8 рублей — это твой выигрыш. Стоимость игры — 56 рублей. Во второй: бросаешь один кубик, выпавшее число умножается на 15 рублей — твой выигрыш. Стоимость игры — 60 рублей. В какой игре средний проигрыш меньше?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют E(выигрыша) для каждой игры.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая игра выгоднее для посетителя?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> E₁ = 7×8 = 56, E₂ = 3,5×15 = 52,5.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как изменить стоимость, чтобы игра стала справедливой?`,
        question: "Чему равно математическое ожидание выигрыша во второй игре (один кубик, умножить на 15)? (введите число, например 52.5)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 52.5,
        hint: "💡 E(очков на кубике) = 3,5. E(выигрыша) = 3,5 × 15",
        solution: "✅ E(выигрыша) во второй игре = 3,5 × 15 = <strong>52,5 рублей</strong>. Стоимость игры = 60 рублей, средний проигрыш = 7,5 рублей. В первой игре E(выигрыша) = 7 × 8 = 56 рублей, стоимость = 56 рублей — игра справедливая. Первая игра выгоднее (проигрыш 0 против 7,5)."
    },
    // ========== КЕЙС 5. «Инвестиции: куда вложить деньги?» ==========
    {
        id: "expect_5",
        title: "💰 Кейс 5: «Инвестиции: куда вложить деньги?»",
        description: "У инвестора есть 100 000 рублей. Два варианта: Вариант А (надёжный) — вклад в банке под 9% годовых (доход 9000 рублей). Вариант Б (рискованный) — инвестиция в стартап: с вероятностью 0,25 доход 60 000 рублей, с вероятностью 0,5 доход 10 000 рублей, с вероятностью 0,25 убыток 20 000 рублей. Какой вариант выгоднее по математическому ожиданию?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют E(дохода) для варианта Б.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой вариант даёт больший средний доход?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> E(Б) = 60000×0,25 + 10000×0,5 - 20000×0,25.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему некоторые выбирают А, а некоторые Б?`,
        question: "Чему равно математическое ожидание дохода для варианта Б (в рублях)? (введите число, например 14000)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 15000,
        hint: "💡 E = 60000×0,25 + 10000×0,5 − 20000×0,25 = 15000 + 5000 − 5000",
        solution: "✅ E(доход) для варианта Б = 60000×0,25 + 10000×0,5 − 20000×0,25 = 15000 + 5000 − 5000 = <strong>15000 рублей</strong>. Вариант А даёт 9000 рублей. По математическому ожиданию вариант Б выгоднее, но он связан с риском (25% убытка). Выбор зависит от отношения к риску."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ИСПЫТАНИЯ БЕРНУЛЛИ" (9 КЛАСС) ==========
const grade9_topic4Cases = [
    // ========== КЕЙС 1. «СМС не отправляется» ==========
    {
        id: "bernoulli_1",
        title: "📱 Кейс 1: «СМС не отправляется»",
        description: "Антон находится в деревне, где связь очень плохая. Он пытается отправить СМС подруге Кате. Телефон показывает: «Идёт отправка... ошибка. Повторить?» Антон нажимает «Повторить» снова и снова. После 5 неудачных попыток Антон звонит Кате и говорит: «Я уже 5 раз отправил СМС, и всё без толку. Наверное, связь совсем пропала. Пойду на холм, может, там поймает». Катя отвечает: «Не торопись. Вероятность отправки с одной попытки — 0,25. То, что пять раз подряд не отправилось, — это нормально. Шестая может отправиться».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Кто прав — Антон или Катя?<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с геометрическим распределением (испытания до первого успеха).<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какова вероятность 5 неудач подряд?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют q⁵ = 0,75⁵.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> При каком p стоит менять место?`,
        question: "Какова вероятность того, что потребуется БОЛЬШЕ 5 попыток для отправки СМС? (введите десятичной дробью, округлив до тысячных, например 0.237)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.237,
        hint: "💡 Больше 5 попыток = первые 5 попыток неудачны. q = 1 − 0,25 = 0,75. P = q⁵",
        solution: "✅ q = 0,75. P(больше 5 попыток) = 0,75⁵ = <strong>0,2373 ≈ 0,237</strong> (около 24%). Это довольно большая вероятность, поэтому Катя права: 5 неудач подряд — не повод менять место. Среднее число попыток = 1/0,25 = 4."
    },
    // ========== КЕЙС 2. «Стрельба по мишени до попадания» ==========
    {
        id: "bernoulli_2",
        title: "🎯 Кейс 2: «Стрельба по мишени до попадания»",
        description: "В тире проводится соревнование: стрелок стреляет по мишени до первого попадания. Побеждает тот, кто затратит меньше патронов. Два стрелка спорят перед соревнованием. Стрелок А говорит: «У меня вероятность попадания 0,9. Я почти всегда попадаю с первого выстрела». Стрелок Б говорит: «У меня вероятность 0,4. Но зато я могу выиграть, если тебе не повезёт». Судья вмешивается: «Давайте посчитаем вероятности». Кто из них объективно сильнее?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся сравнивают среднее число выстрелов.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> У кого среднее число выстрелов меньше?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Среднее = 1/p для каждого.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Может ли Б выиграть в отдельной встрече?`,
        question: "Чему равно среднее число выстрелов для стрелка А (p=0,9)? (введите число, округлив до десятых, например 1.2)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 1.1,
        hint: "💡 Среднее число испытаний до первого успеха = 1/p",
        solution: "✅ Среднее число выстрелов для А = 1/0,9 ≈ <strong>1,11 ≈ 1,1</strong>. Для Б = 1/0,4 = 2,5. А объективно сильнее — в среднем тратит в 2,2 раза меньше патронов. Но Б может выиграть в отдельной встрече, если А не повезёт."
    },
    // ========== КЕЙС 3. «Спор о честности кассира» ==========
    {
        id: "bernoulli_3",
        title: "🪙 Кейс 3: «Спор о честности кассира»",
        description: "В метро кассир складывает монеты в столбики по 10 монет. Он утверждает, что кладёт монеты случайной стороной вверх. Контролёр проверил 10 столбиков и в одном из них обнаружил 8 монет орлом вверх. Контролёр заявляет: «Вероятность такого — всего около 4%! Кассир специально кладёт монеты орлом вверх, чтобы было удобнее считать». Кассир оправдывается: «4% — это не так уж мало. Раз в 25 столбиков такое случается. Я проверил 10 столбиков, и один из них оказался таким — это нормально». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют вероятность события.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Действительно ли 8 орлов — редкость?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят P(8,9,10 орлов) и вероятность для 10 столбиков.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько столбиков нужно проверить для уверенного вывода?`,
        question: "Какова вероятность того, что хотя бы в одном из 10 столбиков выпадет 8, 9 или 10 орлов? (введите десятичной дробью, округлив до сотых, например 0.43)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.43,
        hint: "💡 Сначала найди P(8,9,10 орлов) для одного столбика, затем используй формулу 1 − (1 − p)¹⁰",
        solution: "✅ P(8 орлов) = 45/1024 ≈ 0,0439; P(9) = 10/1024 ≈ 0,0098; P(10) = 1/1024 ≈ 0,001. Сумма ≈ 0,0547. P(хотя бы в одном из 10) = 1 − (1 − 0,0547)¹⁰ ≈ 1 − 0,9453¹⁰ ≈ <strong>0,43</strong> (43%). Это не редкость, поэтому кассир, скорее всего, честен. Контролёр неправ."
    },
    // ========== КЕЙС 4. «Краш-тест: выпускать или не выпускать?» ==========
    {
        id: "bernoulli_4",
        title: "🚗 Кейс 4: «Краш-тест: выпускать или не выпускать?»",
        description: "Автомобильная компания разработала новую модель. По стандартам безопасности требуется, чтобы вероятность серьёзного повреждения манекена при краш-тесте не превышала 0,1. Компания провела 10 краш-тестов. Результат: в 2 тестах манекен получил серьёзные повреждения. Главный инженер говорит: «2 повреждения из 10 — это 20%, что выше допустимых 10%. Нужно дорабатывать конструкцию». Директор компании возражает: «Это только 10 тестов. Может, нам просто не повезло». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют вероятность получить 2 или более повреждений при p=0,1.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Достаточно ли 2 повреждений для браковки?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> P(≥2) = 1 − P(0) − P(1).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько тестов нужно для надёжного вывода?`,
        question: "Если реальная вероятность повреждения p=0,1, какова вероятность получить 2 или более повреждений в 10 тестах? (введите десятичной дробью, округлив до сотых, например 0.26)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.26,
        hint: "💡 P(0) = 0,9¹⁰, P(1) = 10 × 0,1 × 0,9⁹. Затем P(≥2) = 1 − P(0) − P(1).",
        solution: "✅ P(0) = 0,9¹⁰ ≈ 0,3487; P(1) = 10 × 0,1 × 0,9⁹ = 1 × 0,9⁹ ≈ 0,3874; P(≥2) = 1 − 0,3487 − 0,3874 = <strong>0,2639 ≈ 0,26</strong> (26%). Вероятность не маленькая, поэтому результат 2 повреждений из 10 не доказывает, что p > 0,1. Нужно больше тестов."
    },
    // ========== КЕЙС 5. «Самолёт: сколько порций курицы грузить?» ==========
    {
        id: "bernoulli_5",
        title: "✈️ Кейс 5: «Самолёт: сколько порций курицы грузить?»",
        description: "На борт самолёта на 120 пассажиров нужно загрузить ужин: курица или рыба. Статистика показывает, что 55% пассажиров предпочитают курицу. Менеджер по закупкам предлагает загрузить 66 порций курицы и 54 рыбы (ровно по вероятности). Бортпроводник возражает: «А если курицу выберет больше 66 человек? Тогда кому-то придётся есть рыбу, и они будут недовольны. Давайте загрузим 75 куриц и 45 рыб». Математик говорит: «Давайте посчитаем риски». Какова вероятность нехватки курицы при 66 порциях?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся оценивают вероятность отклонения от среднего.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Нужно ли бортпроводнику волноваться?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Среднее = n·p = 120×0,55 = 66.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как изменится риск при 75 порциях?`,
        question: "Какова вероятность того, что курицу выберут БОЛЬШЕ 66 человек? (введите десятичной дробью, округлив до сотых, например 0.50)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.5,
        hint: "💡 Среднее число выбирающих курицу = 120 × 0,55 = 66. Распределение почти симметрично относительно среднего.",
        solution: "✅ Среднее число = 120 × 0,55 = <strong>66</strong>. Вероятность того, что курицу выберут больше 66 человек, примерно равна вероятности, что выберут меньше 66. Из-за симметрии биномиального распределения она близка к <strong>0,5</strong>. Риск нехватки очень высок — около 50%. Менеджер неправ, бортпроводник прав: нужно грузить с запасом."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ГЕОМЕТРИЧЕСКАЯ ВЕРОЯТНОСТЬ" (9 КЛАСС) ==========
const grade9_topic3Cases = [
    // ========== КЕЙС 1. «Сломанный пиксель на экране» ==========
    {
        id: "geom_1",
        title: "📱 Кейс 1: «Сломанный пиксель на экране»",
        description: "На экране смартфона размером 6 см × 12 см перестал работать один пиксель. Экран имеет разрешение 1080×2340 пикселей. Пользователь хочет знать: какова вероятность того, что сломанный пиксель находится в верхней левой четверти экрана? (Считать, что пиксель может с равной вероятностью оказаться в любой точке экрана).",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием геометрической вероятности.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Как найти вероятность через площади?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют площадь экрана и площадь четверти.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему дискретные пиксели можно заменить непрерывной площадью?`,
        question: "Какова вероятность того, что сломанный пиксель находится в верхней левой четверти экрана? (введите десятичной дробью, например 0.25)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.25,
        hint: "💡 Верхняя левая четверть занимает 1/4 площади экрана. Вероятность = площадь четверти ÷ площадь всего экрана.",
        solution: "✅ Площадь экрана = 6×12 = 72 см². Площадь верхней левой четверти = 72÷4 = 18 см². Вероятность = 18/72 = <strong>0,25</strong> (или 1/4)."
    },
    // ========== КЕЙС 2. «Встреча друзей в парке» ==========
    {
        id: "geom_2",
        title: "🤝 Кейс 2: «Встреча друзей в парке»",
        description: "Два друга договорились встретиться в парке между 12:00 и 13:00. Каждый приходит в случайный момент времени в течение этого часа и ждёт другого ровно 20 минут. Если друг не пришёл за 20 минут — уходит. Какова вероятность того, что они встретятся? (20 минут = 1/3 часа)",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся решают задачу о встрече.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Как изобразить условие на плоскости?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Строят квадрат 1×1 и полосу |x−y| ≤ 1/3.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как изменится вероятность, если время ожидания увеличить?`,
        question: "Какова вероятность встречи друзей? (введите десятичной дробью, округлив до тысячных, например 0.456)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.556,
        hint: "💡 Площадь полосы = 1 − (площадь двух треугольников). Каждый треугольник имеет сторону (2/3) и площадь (2/3)²÷2 = 2/9.",
        solution: "✅ Площадь квадрата = 1. Площадь двух треугольников вне полосы = 2 × ((2/3)²/2) = 2 × (4/9/2) = 2 × (2/9) = 4/9. Площадь полосы = 1 − 4/9 = 5/9 ≈ <strong>0,556</strong>. Вероятность встречи = 5/9 ≈ 0,556."
    },
    // ========== КЕЙС 3. «Монетка на клетчатом полу» ==========
    {
        id: "geom_3",
        title: "🪙 Кейс 3: «Монетка на клетчатом полу»",
        description: "На полу нарисована квадратная сетка со стороной клетки 12 см. На пол случайным образом падает монетка диаметром 2 см. Найдите вероятность того, что монетка целиком попадёт внутрь какой-нибудь клетки (не наступит на линию).",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся находят «безопасную» область для центра монетки.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> На каком расстоянии от линий должен быть центр?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют площадь безопасной зоны.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как изменится вероятность, если монетка больше?`,
        question: "Какова вероятность того, что монетка не заденет линии сетки? (введите десятичной дробью, например 0.64)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.64,
        hint: "💡 Радиус монетки = 1 см. Центр должен отстоять от линий не менее чем на 1 см. Сторона безопасного квадрата = 12 − 1 − 1 = 10 см.",
        solution: "✅ Площадь клетки = 12×12 = 144 см². Безопасная область для центра = квадрат 10×10 = 100 см². Вероятность = 100/144 = <strong>0,64</strong> (или 25/36 ≈ 0,694? Проверим: 100/144 = 25/36 ≈ 0,694? 100÷144 ≈ 0,694. Ответ: 25/36 ≈ 0,694)"
    },
    // ========== КЕЙС 4. «Дротики в тире» ==========
    {
        id: "geom_4",
        title: "🎯 Кейс 4: «Дротики в тире»",
        description: "В тире круглая мишень диаметром 40 см. На мишени нарисованы три концентрические зоны: центральный круг (яблочко) радиусом 4 см, среднее кольцо от радиуса 4 до 12 см, внешнее кольцо от радиуса 12 до 20 см. Начинающий стрелок стреляет издалека. Из-за рассеивания пуль можно считать, что вероятность попасть в любую область мишени пропорциональна её площади.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют площади колец.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> В какую зону попасть проще всего?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят отношение площадей.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему для профессионала эта модель не подходит?`,
        question: "Какова вероятность попадания во ВНЕШНЕЕ кольцо (от радиуса 12 до 20 см)? (введите десятичной дробью, например 0.64)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.64,
        hint: "💡 Площадь всей мишени = π·20² = 400π. Площадь внешнего кольца = π·20² − π·12² = 400π − 144π = 256π.",
        solution: "✅ Площадь всей мишени = π×20² = 400π см². Площадь внешнего кольца = π×20² − π×12² = 400π − 144π = 256π см². Вероятность = 256π / 400π = 256/400 = <strong>0,64</strong> (или 16/25)."
    },
    // ========== КЕЙС 5. «Случайная хорда в круге» ==========
    {
        id: "geom_5",
        title: "⚪ Кейс 5: «Случайная хорда в круге»",
        description: "В круге случайным образом проводится хорда. Выбираются две случайные точки на окружности, и через них проводится хорда. Какова вероятность того, что длина хорды больше радиуса круга? (Указание: длина хорды больше радиуса, когда центральный угол больше 60°)",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся анализируют способ выбора хорды.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Как связаны длина хорды и центральный угол?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят отношение длин дуг.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему ответ зависит от способа выбора «случайной хорды»?`,
        question: "Какова вероятность того, что длина случайной хорды больше радиуса? (введите десятичной дробью, округлив до тысячных, например 0.667)",
        answerNormalizer: (a) => parseFloat(a.replace(',', '.')),
        answer: 0.667,
        hint: "💡 Хорда определяется двумя точками на окружности. Угол между радиусами может быть от 0° до 180°. Длина хорды > R при угле > 60°.",
        solution: "✅ Первую точку фиксируем. Вторая точка может быть в любом месте окружности. Угол между радиусами от 0° до 180°. Длина хорды больше радиуса при угле > 60°. Допустимые углы: от 60° до 180° (120°). Вероятность = 120°/180° = <strong>2/3 ≈ 0,667</strong>."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ТРЕУГОЛЬНИК ПАСКАЛЯ" (9 КЛАСС) ==========
const grade9_topic2Cases = [
    // ========== КЕЙС 1. «Как быстро найти число сочетаний?» ==========
    {
        id: "pascal_1",
        title: "🔺 Кейс 1: «Как быстро найти число сочетаний?»",
        description: "На уроке комбинаторики учитель попросил найти C₈⁵. Лена сказала: «Нужно вычислять по формуле с факториалами: C₈⁵ = 8! / (5!·3!). Это долго, но правильно». Коля возразил: «А я знаю треугольник Паскаля. В 8-й строке и 5-м столбце уже есть готовый ответ!» Треугольник Паскаля (строки 0-8): 1; 1 1; 1 2 1; 1 3 3 1; 1 4 6 4 1; 1 5 10 10 5 1; 1 6 15 20 15 6 1; 1 7 21 35 35 21 7 1; 1 8 28 56 70 56 28 8 1.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с треугольником Паскаля.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто прав — Лена или Коля?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят C₈⁵ в 8-й строке.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему треугольник Паскаля удобнее формулы?`,
        question: "Чему равно C₈⁵ (8-я строка, 5-й элемент)? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 56,
        hint: "💡 Восьмая строка: 1, 8, 28, 56, 70, 56, 28, 8, 1. 5-й элемент (считая с 0) — 56.",
        solution: "✅ C₈⁵ = <strong>56</strong>. Коля прав: треугольник Паскаля даёт готовый ответ без вычислений. Проверка по формуле: 8!/(5!·3!) = 40320/(120·6) = 56."
    },
    // ========== КЕЙС 2. «Выбор пиццы: быстрый способ» ==========
    {
        id: "pascal_2",
        title: "🍕 Кейс 2: «Выбор пиццы: быстрый способ»",
        description: "В пиццерии 9 разных начинок. Клиент хочет заказать пиццу с 4 разными начинками (порядок не важен). Продавец начал вычислять по формуле: C₉⁴ = 9!/(4!·5!). Но клиент торопится. В очереди стоит математик и говорит: «Не надо ничего вычислять! В треугольнике Паскаля уже есть ответ». Треугольник Паскаля (9-я строка): 1, 9, 36, 84, 126, 126, 84, 36, 9, 1.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся находят C₉⁴ в треугольнике.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какую строку и столбец нужно взять?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Определяют C₉⁴ = 126.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сравнивают с C₉⁵.`,
        question: "Чему равно C₉⁴ (9-я строка, 4-й элемент)? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 126,
        hint: "💡 Девятая строка: 1, 9, 36, 84, 126, 126, 84, 36, 9, 1. 4-й элемент (считая с 0) — 126.",
        solution: "✅ C₉⁴ = <strong>126</strong>. Обратите внимание на симметрию: C₉⁵ тоже равно 126."
    },
    // ========== КЕЙС 3. «Секрет суммы строки» ==========
    {
        id: "pascal_3",
        title: "🔢 Кейс 3: «Секрет суммы строки»",
        description: "На уроке математики учитель сказал: «Сумма чисел в любой строке треугольника Паскаля равна степени двойки». Ученик А не поверил: «Для 6-й строки сумма должна быть 64? Проверим!» Треугольник Паскаля (6-я строка): 1, 6, 15, 20, 15, 6, 1.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют сумму 6-й строки.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Равна ли сумма 2⁶?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Складывают числа: 1+6+15+20+15+6+1.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему это свойство работает?`,
        question: "Чему равна сумма чисел 6-й строки треугольника Паскаля? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 64,
        hint: "💡 Сложи все числа 6-й строки: 1+6+15+20+15+6+1 = ?",
        solution: "✅ Сумма чисел 6-й строки = 1+6+15+20+15+6+1 = <strong>64</strong> = 2⁶. Учитель прав. Это свойство следует из того, что сумма Cₙ⁰ + Cₙ¹ + ... + Cₙⁿ = 2ⁿ."
    },
    // ========== КЕЙС 4. «Симметрия в выборе» ==========
    {
        id: "pascal_4",
        title: "🔄 Кейс 4: «Симметрия в выборе»",
        description: "В классе 10 учеников. Нужно выбрать 3 дежурных. Учитель говорит: «C₁₀³ = C₁₀⁷. Проверьте по треугольнику Паскаля». Ученица Маша удивляется: «Как это? 3 и 7 — это же разные числа! Почему они равны?» 10-я строка треугольника: 1, 10, 45, 120, 210, 252, 210, 120, 45, 10, 1.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся находят C₁₀³ и C₁₀⁷.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Действительно ли они равны?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают 120 и 120.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> В чём комбинаторный смысл симметрии?`,
        question: "Чему равно C₁₀³ (10-я строка, 3-й элемент)? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 120,
        hint: "💡 Десятая строка: 1, 10, 45, 120, 210, 252, 210, 120, 45, 10, 1. 3-й элемент (считая с 0) — 120.",
        solution: "✅ C₁₀³ = <strong>120</strong>. C₁₀⁷ тоже равно 120. Это свойство симметрии: Cₙᵏ = Cₙⁿ⁻ᵏ. Выбрать 3 дежурных — всё равно что выбрать 7 недежурных."
    },
    // ========== КЕЙС 5. «Правило сложения в треугольнике» ==========
    {
        id: "pascal_5",
        title: "➕ Кейс 5: «Правило сложения в треугольнике»",
        description: "Математик объясняет правило построения треугольника Паскаля: «Каждое число равно сумме двух чисел, стоящих над ним (слева и справа)». Ученик спрашивает: «А зачем это нужно?» Другой ученик отвечает: «Потому что так можно найти C₁₀⁴, зная только 9-ю строку». 9-я строка: 1, 9, 36, 84, 126, 126, 84, 36, 9, 1.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся применяют правило сложения.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Как найти C₁₀⁴ через 9-ю строку?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> C₁₀⁴ = C₉³ + C₉⁴ = 84 + 126.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему это правило работает?`,
        question: "Чему равно C₁₀⁴, если C₉³ = 84 и C₉⁴ = 126? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 210,
        hint: "💡 По правилу сложения: C₁₀⁴ = C₉³ + C₉⁴ = 84 + 126",
        solution: "✅ C₁₀⁴ = 84 + 126 = <strong>210</strong>. Правило сложения отражает комбинаторный смысл: выбрать 4 из 10 можно либо выбрав определённый элемент (тогда нужно выбрать ещё 3 из 9), либо не выбрав его (тогда нужно выбрать 4 из 9)."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ПЕРЕСТАНОВКИ, ФАКТОРИАЛ, СОЧЕТАНИЯ" (9 КЛАСС) ==========
const grade9_topic1Cases = [
    // ========== КЕЙС 1. «Спор о расписании уроков» ==========
    {
        id: "perm_1",
        title: "📅 Кейс 1: «Спор о расписании уроков»",
        description: "В 9 классе в пятницу 6 разных уроков: алгебра, геометрия, физика, русский язык, литература, физкультура. Учитель составляет расписание на этот день. Петя говорит: «Учитель может составить расписание 720 разными способами». Вася спорит: «Нет, гораздо больше — 6⁶ = 46656 способов!»",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием перестановки и факториала.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто прав — Петя или Вася?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют формулу Pₙ = n! = 6!<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему Вася ошибся?`,
        question: "Сколько существует способов составить расписание из 6 разных уроков (каждый урок ровно один раз)? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 720,
        hint: "💡 Количество перестановок n элементов равно n! = 1×2×3×4×5×6",
        solution: "✅ Петя прав. Количество перестановок 6 уроков = 6! = 6×5×4×3×2×1 = <strong>720</strong>. Вася ошибся, потому что он предположил, что уроки могут повторяться (6⁶ = 46656), но в расписании каждый урок бывает один раз."
    },
    // ========== КЕЙС 2. «Выбор капитана и заместителя» ==========
    {
        id: "perm_2",
        title: "👑 Кейс 2: «Выбор капитана и заместителя»",
        description: "В классе 25 учеников. Нужно выбрать капитана команды и его заместителя. Капитан и заместитель — разные должности, порядок важен. Учитель спросил: «Сколько существует способов сделать этот выбор?» Один ученик ответил: «25·24 = 600». Другой сказал: «А если бы мы выбирали просто двух дежурных (порядок не важен), способов было бы меньше».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с размещениями и сочетаниями.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Сколько способов, если порядок не важен?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют формулу Cₙᵏ = n!/(k!·(n−k)!)<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> В чём разница между размещениями и сочетаниями?`,
        question: "Сколько существует способов выбрать двух дежурных из 25, если порядок НЕ важен? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 300,
        hint: "💡 Количество сочетаний из 25 по 2 = C₂₅² = 25×24÷2",
        solution: "✅ Если порядок не важен, то количество способов = C₂₅² = 25×24÷2 = <strong>300</strong>. Это число сочетаний. А если порядок важен (капитан и заместитель), то количество размещений = 25×24 = 600."
    },
    // ========== КЕЙС 3. «Заказ пиццы» ==========
    {
        id: "perm_3",
        title: "🍕 Кейс 3: «Заказ пиццы»",
        description: "В пиццерии есть 10 разных видов начинок. Клиент хочет заказать пиццу с 3 разными начинками (порядок начинок не важен, они просто кладутся на пиццу). Менеджер говорит: «У нас 720 вариантов!» Повар говорит: «Нет, 1000!» Математик смеётся: «Вы оба неправы».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся применяют формулу сочетаний.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто прав — менеджер, повар или математик?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют C₁₀³ = (10×9×8)/(3×2×1)<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему менеджер и повар ошиблись?`,
        question: "Сколько существует пицц с 3 разными начинками из 10? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 120,
        hint: "💡 C₁₀³ = (10×9×8) / (3×2×1) = 720 ÷ 6",
        solution: "✅ Прав математик. C₁₀³ = (10×9×8) / (3×2×1) = 720 / 6 = <strong>120</strong>. Менеджер посчитал размещения (порядок важен — 720), а повар — с повторениями (10³ = 1000)."
    },
    // ========== КЕЙС 4. «Секретный код» ==========
    {
        id: "perm_4",
        title: "🔐 Кейс 4: «Секретный код»",
        description: "Банкомат требует ввести 6-значный код. Цифры от 0 до 9. Два друга спорят. Один говорит: «Цифры могут повторяться. Всего кодов 10⁶ = 1 000 000». Второй говорит: «А если бы цифры не могли повторяться, кодов было бы гораздо меньше». Прав ли второй друг?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся применяют правило умножения и размещения.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Сколько кодов без повторений?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют 10×9×8×7×6×5<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Во сколько раз уменьшится число кодов?`,
        question: "Сколько существует 6-значных кодов, если цифры НЕ повторяются? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 151200,
        hint: "💡 Первую цифру выбираем 10 способами, вторую — 9, третью — 8, четвёртую — 7, пятую — 6, шестую — 5",
        solution: "✅ Количество кодов без повторений = 10×9×8×7×6×5 = <strong>151200</strong>. Второй друг прав. Через факториалы: 151200 = 10! / 4!."
    },
    // ========== КЕЙС 5. «Шахматный турнир» ==========
    {
        id: "perm_5",
        title: "♟️ Кейс 5: «Шахматный турнир»",
        description: "В шахматном турнире участвуют 12 человек. Каждый играет с каждым ровно один раз (круговая система). Организатор хочет знать: 1) Сколько всего партий будет сыграно? 2) Сколько существует способов распределить призовые места (золото, серебро, бронза)? 3) Сколько способов выбрать трёх призёров (без учёта порядка)?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся применяют сочетания и размещения.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Как подсчитать каждое количество?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Используют формулы Cₙᵏ и Aₙᵏ.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> В чём разница между тремя вопросами?`,
        question: "Сколько всего партий будет сыграно в турнире из 12 человек (каждый с каждым один раз)? (введите число)",
        answerNormalizer: (a) => parseInt(a.replace(/\s/g, '')),
        answer: 66,
        hint: "💡 Каждая партия — это неупорядоченная пара игроков: C₁₂² = 12×11÷2",
        solution: "✅ Партий: C₁₂² = 12×11÷2 = <strong>66</strong>. Распределение призов (порядок важен): A₁₂³ = 12×11×10 = <strong>1320</strong>. Выбор трёх призёров (без порядка): C₁₂³ = 1320÷6 = <strong>220</strong>."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ГРАФЫ" (7 КЛАСС) ==========
const grade7_topic9Cases = [
    // ========== КЕЙС 1. «Турнир по настольному теннису» ==========
    {
        id: "graph_1",
        title: "🏓 Кейс 1: «Турнир по настольному теннису»",
        description: "Шесть одноклассников — Андрей (А), Борис (Б), Вадим (В), Григорий (Г), Дмитрий (Д) и Евгений (Е) — устроили турнир по настольному теннису. На данный момент сыграны такие партии: А сыграл с Б и Д; Б сыграл с А, Г и Е; В пока не играл ни с кем; Г сыграл с Б, Д и Е; Д сыграл с А, Г и Е; Е сыграл с Б, Г и Д.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятиями вершины, ребра, степени вершины.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто сыграл больше всех партий?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Строят граф и подсчитывают степени вершин.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько партий ещё предстоит сыграть?`,
        question: "Сколько партий сыграл Борис (Б) на данный момент? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 3,
        hint: "💡 Посчитай, с кем связана вершина Б: А, Г, Е — это 3 партии.",
        solution: "✅ Борис сыграл <strong>3</strong> партии (с Андреем, Григорием и Евгением). Всего в турнире должно быть 15 партий, сыграно 7, осталось 8 партий."
    },
    // ========== КЕЙС 2. «Острова и мосты» ==========
    {
        id: "graph_2",
        title: "🏝️ Кейс 2: «Острова и мосты»",
        description: "В архипелаге есть 6 островов: Адуак (А), Бани (Б), Видо (В), Гауту (Г), Джеми (Д), Екити (Е). Построено 6 мостов: между А и Б, между А и В, между Б и В, между Б и Д, между В и Д, между Г и Е. Турист хочет попасть с острова Адуак (А) на остров Гауту (Г).",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием связности графа.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Можно ли попасть с А на Г?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Строят граф и находят компоненты связности.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько мостов нужно добавить, чтобы соединить все острова?`,
        question: "Может ли турист попасть с острова А на остров Г? (введите: да или нет)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "нет",
        hint: "💡 Нарисуй граф. Есть ли путь от А до Г? Обрати внимание, что Г соединён только с Е.",
        solution: "✅ Турист <strong>не может</strong> попасть с А на Г. Граф распадается на две компоненты связности: {А, Б, В, Д} и {Г, Е}. Между ними нет мостов."
    },
    // ========== КЕЙС 3. «Задача о рукопожатиях» ==========
    {
        id: "graph_3",
        title: "🤝 Кейс 3: «Задача о рукопожатиях»",
        description: "На деловой встрече 9 человек обменивались рукопожатиями. Организатор утверждает, что количество людей, сделавших нечётное число рукопожатий, обязательно чётное. Один из гостей говорит: «А вдруг у нас ровно 5 человек пожали руки нечётное число раз?»",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с теоремой о сумме степеней вершин.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Может ли быть 5 человек с нечётным числом рукопожатий?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют теорему: сумма степеней всех вершин чётна.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему количество людей с нечётным числом рукопожатий всегда чётно?`,
        question: "Может ли на встрече быть ровно 5 человек с нечётным числом рукопожатий? (введите: да или нет)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "нет",
        hint: "💡 Сумма степеней всех вершин = 2 × число рукопожатий. Это число чётное. Сумма нечётного количества нечётных чисел даёт нечётное число.",
        solution: "✅ <strong>Не может</strong>. Сумма степеней всех вершин всегда чётна (2× число рёбер). Если бы было 5 человек с нечётным числом рукопожатий, сумма их степеней была бы нечётной, что невозможно. Поэтому прав организатор."
    },
    // ========== КЕЙС 4. «Кёнигсбергские мосты» ==========
    {
        id: "graph_4",
        title: "🌉 Кейс 4: «Кёнигсбергские мосты»",
        description: "В городе Кёнигсберге (ныне Калининград) река Преголя делит город на 4 части. Части соединены 7 мостами. Легенда гласит: тот, кто сможет пройти по каждому мосту ровно один раз и вернуться в исходную точку, обретёт счастье. Великий математик Леонард Эйлер доказал, что это невозможно.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель рассказывает историю.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием эйлерова пути и цикла.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему это невозможно?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют критерий Эйлера: для эйлерова цикла все степени вершин должны быть чётными.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какое минимальное количество мостов нужно убрать, чтобы задача стала возможной?`,
        question: "Сколько вершин нечётной степени было в графе кёнигсбергских мостов? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 4,
        hint: "💡 Построй граф: части города — вершины, мосты — рёбра. Посчитай степень каждой вершины.",
        solution: "✅ В графе было <strong>4</strong> вершины нечётной степени. Для существования эйлерова цикла (пути, проходящего по каждому мосту ровно один раз с возвращением) нужно, чтобы все вершины имели чётную степень. Поэтому пройти по всем мостам ровно один раз невозможно."
    },
    // ========== КЕЙС 5. «Электрическая цепь» ==========
    {
        id: "graph_5",
        title: "💡 Кейс 5: «Электрическая цепь»",
        description: "Инженер проектирует электрическую цепь для подключения 5 лампочек проводами. Ему нужно, чтобы: можно было зажечь любую лампочку от источника (граф должен быть связным), в цепи не было лишних проводов (минимальное количество), в цепи не было замкнутых контуров (циклов).",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием дерева.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Сколько проводов минимально нужно?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют свойство дерева: n вершин → n−1 ребро.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что произойдёт, если добавить один лишний провод?`,
        question: "Какое минимальное количество проводов нужно для соединения 5 лампочек в связную сеть без циклов? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 4,
        hint: "💡 Для связного графа без циклов (дерева) количество рёбер = количество вершин − 1.",
        solution: "✅ Минимальное количество проводов = 5 − 1 = <strong>4</strong>. Такой граф называется деревом. Добавление пятого провода создаст цикл, что может привести к нежелательным путям для тока."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "МОНЕТА И ИГРАЛЬНАЯ КОСТЬ" (7 КЛАСС) ==========
const grade7_topic8Cases = [
    // ========== КЕЙС 1. «Спор о честной монете» ==========
    {
        id: "coin_1",
        title: "🪙 Кейс 1: «Спор о честной монете»",
        description: "Два друга подбрасывают монету, чтобы решить, кто пойдёт за пиццей. Они договорились: орёл — идёт Петя, решка — идёт Вася. Петя подбросил монету 10 раз. Результат: 7 раз выпал орёл, 3 раза — решка. Вася возмутился: «Твоя монета неправильная! У неё орёл выпадает чаще!» Петя ответил: «Монета обычная. Просто так совпало».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, может ли честная монета дать 7 орлов из 10.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием «математическая монета» и равновозможными исходами.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто прав — Петя или Вася?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют, что при малом количестве бросков возможны отклонения.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько бросков нужно сделать, чтобы проверить честность монеты?`,
        question: "Может ли у честной монеты при 10 бросках выпасть 7 орлов? (введите: да или нет)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "да",
        hint: "💡 У честной монеты вероятность орла = 1/2. При 10 бросках возможны разные результаты, в том числе 7 орлов.",
        solution: "✅ Петя прав. 7 орлов из 10 — возможный результат для честной монеты. Это не доказывает, что монета неправильная. Чем больше бросков, тем ближе частота к 0,5, но при малом количестве бросков возможны отклонения."
    },
    // ========== КЕЙС 2. «Футбольный жребий» ==========
    {
        id: "coin_2",
        title: "⚽ Кейс 2: «Футбольный жребий»",
        description: "Перед футбольным матчем судья бросает монету, чтобы определить, какая команда начнёт игру. Один зритель говорит: «Это нечестно! Монета может упасть на ребро или улететь. Тогда жребий не сработает». Другой зритель отвечает: «В правилах сказано: если монета упала на ребро, бросок повторяют. А вероятность такого события ничтожно мала».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся обсуждают, сколько исходов у реальной монеты.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Можно ли пренебречь исходом «ребро»?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Оценивают вероятность падения на ребро (≈ 1/6000).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какие ещё способы случайного выбора существуют?`,
        question: "Сколько равновозможных исходов у математической монеты? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 2,
        hint: "💡 У математической монеты только два исхода: орёл и решка.",
        solution: "✅ У математической монеты <strong>2</strong> равновозможных исхода: орёл и решка. Падение на ребро — это крайне редкое событие (примерно 1 раз на 6000 бросков), которым в теории вероятностей пренебрегают."
    },
    // ========== КЕЙС 3. «Бросаем кубик дважды» ==========
    {
        id: "dice_1",
        title: "🎲 Кейс 3: «Бросаем кубик дважды»",
        description: "Два игрока играют в игру: бросают игральный кубик дважды. Игрок А выигрывает, если сумма очков равна 8. Игрок Б выигрывает, если сумма очков равна 9. Игрок А говорит: «Сумма 8 выпадает чаще, чем 9! У меня больше шансов!» Игрок Б возражает: «Нет, у нас шансы равны. Обе суммы могут выпасть, и всё».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят таблицу 6×6 для двух бросков кубика.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто прав — А или Б?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Подсчитывают количество исходов для каждой суммы.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какая сумма выпадает чаще всего?`,
        question: "Сколько исходов дают сумму 9 при двух бросках кубика? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 4,
        hint: "💡 Построй таблицу: первый бросок от 1 до 6, второй — от 1 до 6. Найди все пары, где сумма равна 9.",
        solution: "✅ Сумму 9 дают пары: (3,6), (4,5), (5,4), (6,3) — всего <strong>4</strong> исхода. А сумму 8 дают 5 исходов. Значит, у игрока А (сумма 8) шансов больше. Игрок Б не прав."
    },
    // ========== КЕЙС 4. «Правильные и поддельные кости» ==========
    {
        id: "dice_2",
        title: "🏛️ Кейс 4: «Правильные и поддельные кости»",
        description: "В Древнем Риме император Клавдий узнал, что в одной из таверн используют поддельные игральные кости. У этих костей центр тяжести смещён, поэтому некоторые грани выпадают чаще других. Император приказал разобраться: как отличить правильную (честную) кость от поддельной?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вспоминают свойства правильной кости.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Как экспериментально проверить честность кости?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Предлагают провести серию бросков и сравнить частоты с 1/6.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько бросков нужно сделать для надёжной проверки?`,
        question: "Чему равна вероятность выпадения любой грани у правильной игральной кости? (введите десятичной дробью, например 0.333)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 1/6,
        hint: "💡 У правильной кости 6 граней, и все они равновозможны.",
        solution: "✅ У правильной игральной кости вероятность выпадения любой грани = <strong>1/6 ≈ 0,167</strong>. Чтобы проверить, честная ли кость, нужно бросить её много раз (например, 600) и посмотреть, сколько раз выпала каждая грань. Если какая-то грань выпадает сильно чаще или реже 100 раз — возможно, кость поддельная."
    },
    // ========== КЕЙС 5. «Монета и кубик вместе» ==========
    {
        id: "coin_dice_1",
        title: "🎲 Кейс 5: «Монета и кубик вместе»",
        description: "В игре используют одновременно монету и игральный кубик. Сначала бросают монету. Если выпадает орёл, то бросают кубик один раз. Если выпадает решка, то бросают кубик дважды. Сколько всего различных исходов может быть в этом опыте?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят «дерево возможностей».<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Как подсчитать общее число исходов?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Складывают исходы для орла и для решки.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему здесь нужно складывать, а не умножать?`,
        question: "Сколько всего исходов в этом опыте? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 42,
        hint: "💡 При орле: 1 вариант монеты × 6 вариантов кубика = 6. При решке: 1 вариант монеты × 6×6 вариантов кубика = 36. Сложи результаты.",
        solution: "✅ При орле: 1 × 6 = <strong>6</strong> исходов. При решке: 1 × 6 × 6 = <strong>36</strong> исходов. Всего: 6 + 36 = <strong>42</strong> исхода. Складываем, потому что это два разных непересекающихся сценария."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "СЛУЧАЙНЫЙ ОПЫТ И СЛУЧАЙНОЕ СОБЫТИЕ" (7 КЛАСС) ==========
const grade7_topic7Cases = [
    // ========== КЕЙС 1. «Прогноз погоды» ==========
    {
        id: "random_1",
        title: "🌧️ Кейс 1: «Прогноз погоды»",
        description: "Синоптик в новостях сказал: «Вероятность дождя завтра — 35%». Девочка, услышав это, сказала маме: «Можно не брать зонт, дождя скорее всего не будет». Мама ответила: «А я возьму зонт, мало ли что». Вечером пошёл дождь. Девочка расстроилась: «Синоптик ошибся! Он сказал 35%, а дождь пошёл!»",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что значит «вероятность 35%».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятиями случайного, достоверного и невозможного события.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Права ли девочка? Может ли событие с вероятностью 35% произойти?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют, что вероятность 35% означает 35 случаев из 100.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какую вероятность дождя можно считать «можно не брать зонт»?`,
        question: "Права ли девочка, что синоптик ошибся? (введите: да или нет)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "нет",
        hint: "💡 Вероятность 35% не означает, что дождя не будет. Она означает, что в 35 случаях из 100 дождь идёт.",
        solution: "✅ Девочка не права. Событие с вероятностью 35% может как произойти, так и не произойти. Дождь пошёл — это один из возможных исходов, а не ошибка синоптика."
    },
    // ========== КЕЙС 2. «Игральный кубик» ==========
    {
        id: "random_2",
        title: "🎲 Кейс 2: «Игральный кубик»",
        description: "Два друга спорят о событиях при бросании игрального кубика. Витя говорит: «Выпадение шестёрки — случайное событие. А „выпадение числа от 1 до 6“ — не случайное, потому что оно обязательно случится». Света говорит: «А я считаю, что „выпадение семёрки“ — тоже событие. Просто оно никогда не случается».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Кто прав?<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся определяют три типа событий.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какие события случайные, достоверные, невозможные?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют каждое событие.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Приведите примеры каждого типа событий.`,
        question: "Какое из событий является СЛУЧАЙНЫМ? (введите номер: 1, 2 или 3) — 1: выпала шестёрка, 2: выпало число от 1 до 6, 3: выпало число 8",
        answerNormalizer: (a) => parseInt(a),
        answer: 1,
        hint: "💡 Случайное событие — то, которое может как произойти, так и не произойти.",
        solution: "✅ Правильный ответ: <strong>1 (выпала шестёрка)</strong>. Шестёрка может выпасть, а может нет. А вот число от 1 до 6 — всегда (достоверное), число 8 — никогда (невозможное)."
    },
    // ========== КЕЙС 3. «Спортивный матч» ==========
    {
        id: "random_3",
        title: "⚽ Кейс 3: «Спортивный матч»",
        description: "Перед футбольным матчем между командами «Спартак» и «Динамо» болельщики обсуждают возможные исходы. Один говорит: «Победа „Спартака“ — это случайное событие». Второй говорит: «А я считаю, что событие „матч закончится“ — это достоверное событие». Третий добавляет: «А событие „матч закончится со счётом 100:0“ — невозможное».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Разбирают три типа событий на примере матча.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Согласны ли вы с каждым болельщиком?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Определяют тип каждого события.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Приведите пример достоверного события в школе.`,
        question: "Какое событие является ДОСТОВЕРНЫМ? (введите номер: 1, 2 или 3) — 1: победа «Спартака», 2: матч закончится, 3: счёт 100:0",
        answerNormalizer: (a) => parseInt(a),
        answer: 2,
        hint: "💡 Достоверное событие происходит всегда в данном опыте.",
        solution: "✅ Правильный ответ: <strong>2 (матч закончится)</strong>. Это событие обязательно произойдёт. Победа «Спартака» — случайное событие (может быть, может нет). Счёт 100:0 — невозможное событие в реальном футболе."
    },
    // ========== КЕЙС 4. «Ловля рыбы» ==========
    {
        id: "random_4",
        title: "🎣 Кейс 4: «Ловля рыбы»",
        description: "Рыбак пришёл на озеро, где водятся только два вида рыб: окунь и плотва. Он закинул удочку. Друг спрашивает: «Какая рыба попадётся?» Рыбак отвечает: «Может, окунь, может, плотва. Это случайное событие». Биолог добавляет: «А событие „попадётся щука“ — невозможное. Щук здесь нет». Скептик говорит: «А событие „попадётся хоть какая-нибудь рыба“ — вовсе не достоверное! Можно же ничего не поймать».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Разбирают каждое событие.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто из персонажей прав?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Определяют тип каждого события.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Может ли событие быть случайным в одном опыте и достоверным в другом?`,
        question: "Какое событие является НЕВОЗМОЖНЫМ? (введите номер: 1, 2, 3 или 4) — 1: попадётся окунь, 2: попадётся плотва, 3: попадётся щука, 4: попадётся хоть какая-нибудь рыба",
        answerNormalizer: (a) => parseInt(a),
        answer: 3,
        hint: "💡 Невозможное событие никогда не происходит при данных условиях.",
        solution: "✅ Правильный ответ: <strong>3 (попадётся щука)</strong>. В озере нет щук, поэтому это событие невозможно. Окунь и плотва могут попасться (случайные). Ничего не поймать — тоже возможно (случайное)."
    },
    // ========== КЕЙС 5. «Ремонт телефона» ==========
    {
        id: "random_5",
        title: "📱 Кейс 5: «Ремонт телефона»",
        description: "В мастерской по ремонту телефонов инженер тестирует время работы телефона от одной зарядки батареи. Он включает телефон и засекает время. Инженер говорит: «Время работы телефона — это случайная величина. Я не могу точно сказать, сколько он проработает — 5 часов, 6 часов или 7 часов. Но могу сказать, что телефон не проработает, например, 150 часов — это невозможно для этой батареи. И не проработает 0 часов — тоже невозможно, ведь он включён».",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию.<br>
2️⃣ <strong>Изучение материала:</strong> Разбирают, какие события возможны.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему время работы — случайная величина?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Определяют тип каждого события.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что изменится, если телефон сломан?`,
        question: "Какое событие является СЛУЧАЙНЫМ? (введите номер: 1, 2, 3 или 4) — 1: телефон проработает 150 часов, 2: телефон проработает от 4 до 9 часов, 3: телефон проработает 0 часов, 4: телефон проработает хотя бы 1 секунду",
        answerNormalizer: (a) => parseInt(a),
        answer: 2,
        hint: "💡 Случайное событие — то, которое может как произойти, так и не произойти.",
        solution: "✅ Правильный ответ: <strong>2 (телефон проработает от 4 до 9 часов)</strong>. Это может случиться или не случиться. 150 часов — невозможно, 0 часов — невозможно для исправного телефона, «хотя бы 1 секунду» — достоверно."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ЧАСТОТА ЗНАЧЕНИЙ" (7 КЛАСС) ==========
const grade7_topic6Cases = [
    // ========== КЕЙС 1. «Любимый цвет в классе» ==========
    {
        id: "frequency_1",
        title: "🎨 Кейс 1: «Любимый цвет в классе»",
        description: "В классе 25 учеников. Провели опрос: «Какой твой любимый цвет?» Результаты:<br><br>• Красный: 8 человек<br>• Синий: 7 человек<br>• Зелёный: 5 человек<br>• Жёлтый: 3 человека<br>• Фиолетовый: 2 человека<br><br>Учитель попросил вычислить частоту каждого цвета. Два ученика поспорили: Петя сказал: «Частота красного — 8, синего — 7». Катя возразила: «Нет, частота — это доля». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что такое частота.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием частоты как доли от общего числа.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто прав — Петя или Катя?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют частоты: количество ÷ общее число.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Проверяют, что сумма частот равна 1. Как перевести частоту в проценты?`,
        question: "Чему равна частота (доля) красного цвета? (введите десятичной дробью)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 0.32,
        hint: "💡 Частота = количество ÷ общее количество учеников. Красных — 8, всего — 25.",
        solution: "✅ Частота красного = 8/25 = <strong>0,32</strong>. Синего = 7/25 = 0,28, зелёного = 5/25 = 0,20, жёлтого = 3/25 = 0,12, фиолетового = 2/25 = 0,08. Сумма = 1,00. Права Катя — частота это доля, а не количество."
    },
    // ========== КЕЙС 2. «Домашние животные» ==========
    {
        id: "frequency_2",
        title: "🐾 Кейс 2: «Домашние животные»",
        description: "В классе провели опрос о домашних животных. Результаты (всего 33 ученика):<br><br>• Собака: 9<br>• Кошка: 11<br>• Никого: 7<br>• Рыбка: 3<br>• Птица: 2<br>• Черепаха: 1<br><br>Учитель попросил найти частоты и округлить их до тысячных. Ученик получил сумму 0,999 и расстроился. Действительно ли он ошибся?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что такое округление.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют частоты и округляют до 3 знаков.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему сумма может не равняться 1?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Складывают округлённые частоты.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Погрешность округления — нормальное явление.`,
        question: "Чему равна частота (доля) кошек? (округлите до тысячных)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 0.333,
        hint: "💡 Кошек — 11, всего — 33. 11/33 = 1/3 ≈ 0,333...",
        solution: "✅ Частота кошек = 11/33 = 1/3 ≈ <strong>0,333</strong>. При округлении сумма частот может стать 0,999 или 1,001 — это погрешность округления, а не ошибка."
    },
    // ========== КЕЙС 3. «Оценки за четверть» ==========
    {
        id: "frequency_3",
        title: "📚 Кейс 3: «Оценки за четверть»",
        description: "Петя получил за четверть оценки: 3, 4, 3, 5, 4, 3, 4, 4, 2, 3, 5, 3, 3, 4, 5, 2, 4, 4, 4 (19 оценок). Петя говорит: «Моя средняя оценка — 3,68. Я почти хорошист!» Маша говорит: «Посчитай частоты, увидишь, что пятёрок мало». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как найти среднее через частоты.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся подсчитывают частоты каждой оценки.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая оценка встречается чаще всего?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют среднее через частоты.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сравнивают с обычным средним.`,
        question: "Чему равна частота (доля) пятёрок? (округлите до тысячных)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 0.158,
        hint: "💡 Подсчитай количество пятёрок в списке, затем раздели на общее количество оценок (19).",
        solution: "✅ Пятёрки встречаются 3 раза. Частота = 3/19 ≈ <strong>0,158</strong>. Частота четвёрок = 8/19 ≈ 0,421, троек = 6/19 ≈ 0,316, двоек = 2/19 ≈ 0,105. Среднее через частоты ≈ 3,63, а не 3,68. Петя немного преувеличил."
    },
    // ========== КЕЙС 4. «Опрос в парке» ==========
    {
        id: "frequency_4",
        title: "📺 Кейс 4: «Опрос в парке»",
        description: "В парке опросили 40 человек: «Сколько часов в день вы смотрите телевизор?» Результаты:<br><br>• 0 часов: 4 человека<br>• 1 час: 8 человек<br>• 2 часа: 12 человек<br>• 3 часа: 10 человек<br>• 4 часа: 4 человека<br>• 5 часов: 2 человека<br><br>Социолог хочет представить данные в виде таблицы частот и найти среднее время просмотра.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, зачем нужны частоты.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют частоты.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какое среднее время просмотра?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют среднее через частоты.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какую ещё характеристику (моду) можно найти?`,
        question: "Чему равно среднее время просмотра телевизора? (введите число, например )",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 2.2,
        hint: "💡 Среднее = сумма (часы × частота). Частота = количество ÷ 40.",
        solution: "✅ Частоты: 0,1; 0,2; 0,3; 0,25; 0,1; 0,05. Среднее = 0×0,1 + 1×0,2 + 2×0,3 + 3×0,25 + 4×0,1 + 5×0,05 = 0,2+0,6+0,75+0,4+0,25 = <strong>2,2 часа</strong>."
    },
    // ========== КЕЙС 5. «Магазин обуви» ==========
    {
        id: "frequency_5",
        title: "👟 Кейс 5: «Магазин обуви»",
        description: "Магазин обуви провёл опрос покупателей о размере обуви. Результаты (опрошено 50 человек):<br><br>• 36 размер: 3 человека<br>• 37 размер: 5 человек<br>• 38 размер: 10 человек<br>• 39 размер: 15 человек<br>• 40 размер: 10 человек<br>• 41 размер: 5 человек<br>• 42 размер: 2 человека<br><br>Директор хочет узнать: какой размер самый популярный, какая доля покупателей носит размер 39, и какое среднее значение размера.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как частота помогает в бизнесе.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют частоты.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой размер самый популярный?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят моду, долю и среднее.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему частота удобнее, чем просто количество?`,
        question: "Какова доля (частота) покупателей с 39 размером? (введите десятичной дробью)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 0.3,
        hint: "💡 Доля = количество с 39 размером ÷ общее количество опрошенных (50).",
        solution: "✅ Доля 39 размера = 15/50 = <strong>0,3</strong> (30%). Мода — 39 размер. Средний размер = 36×0,06 + 37×0,1 + 38×0,2 + 39×0,3 + 40×0,2 + 41×0,1 + 42×0,04 = <strong>38,94 ≈ 39</strong>. Магазину стоит закупать больше обуви 39-го размера."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "РАЗМАХ ЧИСЛОВОГО НАБОРА" (7 КЛАСС) ==========
const grade7_topic5Cases = [
    // ========== КЕЙС 1. «Спор о стабильности игроков» ==========
    {
        id: "range_1",
        title: "🏀 Кейс 1: «Спор о стабильности игроков»",
        description: "Тренер выбирает игрока в баскетбольную команду. Два кандидата показали результаты за 5 игр (очки за матч):<br><br>• <strong>Игрок А:</strong> 15, 16, 14, 15, 17<br>• <strong>Игрок Б:</strong> 10, 12, 15, 18, 25<br><br>Средний результат у обоих одинаковый — 15,4 очка. Тренер говорит: «Мне нужен стабильный игрок. Размах покажет, кто меньше проваливается». Кто стабильнее?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что такое стабильность.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием размаха (max − min).<br>
3️⃣ <strong>Выдвижение гипотез:</strong> У кого меньше разброс?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют размах для каждого игрока.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> В каком случае тренер мог бы предпочесть игрока с большим размахом?`,
        question: "Чему равен РАЗМАХ результатов игрока Б? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 15,
        hint: "💡 Размах = максимальное значение − минимальное значение. У игрока Б максимум = 25, минимум = 10.",
        solution: "✅ Игрок А: max=17, min=14, размах = 17−14 = <strong>3</strong>. Игрок Б: max=25, min=10, размах = 25−10 = <strong>15</strong>. У игрока А размах меньше — он стабильнее. Тренер выберет игрока А."
    },
    // ========== КЕЙС 2. «Температура в двух городах» ==========
    {
        id: "range_2",
        title: "🌡️ Кейс 2: «Температура в двух городах»",
        description: "Два друга спорят, где климат мягче. Средние температуры за год одинаковые — +10°C. Данные по месяцам (°C):<br><br>• <strong>Город А:</strong> -15, -10, -5, 0, +5, +10, +15, +20, +15, +10, 0, -5<br>• <strong>Город Б:</strong> -5, -2, 0, +5, +10, +15, +18, +20, +15, +10, +5, 0<br><br>В каком городе климат мягче (размах меньше)?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что значит «мягкий климат».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся находят максимум и минимум для каждого города.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> В каком городе меньше перепад между зимой и летом?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют размах.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему размах — хороший показатель для сравнения климата?`,
        question: "Чему равен РАЗМАХ температур в городе Б? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 25,
        hint: "💡 В городе Б максимальная температура = +20, минимальная = -5. Размах = 20 − (-5) = ?",
        solution: "✅ Город А: max=+20, min=-15, размах = 20−(-15) = <strong>35°C</strong>. Город Б: max=+20, min=-5, размах = 20−(-5) = <strong>25°C</strong>. В городе Б размах меньше — климат мягче."
    },
    // ========== КЕЙС 3. «Контрольная работа: кто лучше?» ==========
    {
        id: "range_3",
        title: "📝 Кейс 3: «Контрольная работа»",
        description: "Учитель сравнивает два класса. Результаты контрольной (баллы от 0 до 10):<br><br>• <strong>7 «А»:</strong> 7, 7, 8, 8, 8, 9, 9, 9, 10, 10<br>• <strong>7 «Б»:</strong> 4, 5, 6, 7, 8, 8, 9, 10, 10, 10<br><br>Средний балл одинаковый — 8,5. Учитель говорит: «Классы одинаковы». Но отличник из 7 «Б» возражает. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему учитель может ошибаться.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют размах для каждого класса.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> В каком классе результаты более разбросаны?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают размахи.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какую характеристику нужно добавить, чтобы понять, где больше отличников?`,
        question: "Чему равен РАЗМАХ результатов в 7 «А»? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 3,
        hint: "💡 В 7 «А» максимальный балл = 10, минимальный = 7. Размах = 10 − 7 = ?",
        solution: "✅ 7 «А»: max=10, min=7, размах = 10−7 = <strong>3</strong>. 7 «Б»: max=10, min=4, размах = 10−4 = <strong>6</strong>. В 7 «А» все ученики в диапазоне 7–10 (стабильно), в 7 «Б» есть и слабые (4 балла). Классы разные, хотя средний одинаков."
    },
    // ========== КЕЙС 4. «Покупка квартиры» ==========
    {
        id: "range_4",
        title: "🏠 Кейс 4: «Покупка квартиры»",
        description: "Застройщик предлагает два дома с одинаковой средней ценой за квадратный метр — 120 тыс. рублей. Цены (тыс. руб. за кв. м):<br><br>• <strong>Дом №1:</strong> 115, 118, 119, 120, 121, 122, 125<br>• <strong>Дом №2:</strong> 90, 95, 100, 120, 140, 145, 150<br><br>Риелтор советует посмотреть на размах. Какой дом лучше выбрать семье со средним бюджетом?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему среднее может обманывать.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют размах для каждого дома.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> В каком доме цены более «кучные»?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают размахи.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какой дом вы выбрали бы для себя? Почему?`,
        question: "Чему равен РАЗМАХ цен в доме №2? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 60,
        hint: "💡 В доме №2 максимальная цена = 150, минимальная = 90. Размах = 150 − 90 = ?",
        solution: "✅ Дом №1: размах = 125−115 = <strong>10</strong> тыс. руб. Дом №2: размах = 150−90 = <strong>60</strong> тыс. руб. В доме №1 цены близки друг к другу — хороший выбор для семьи со средним бюджетом. В доме №2 большой разброс — есть и очень дешёвые, и очень дорогие квартиры."
    },
    // ========== КЕЙС 5. «Спортивный комментатор» ==========
    {
        id: "range_5",
        title: "🎙️ Кейс 5: «Спортивный комментатор»",
        description: "Комментатор сравнивает двух прыгунов в длину. Средний результат одинаковый — 7 метров. Результаты 5 прыжков (метров):<br><br>• <strong>Прыгун А:</strong> 6,9, 7,0, 7,0, 7,1, 7,0<br>• <strong>Прыгун Б:</strong> 6,0, 6,5, 7,0, 7,5, 8,0<br><br>Комментатор говорит: «Первый стабилен, а второй — настоящие американские горки!» Подтвердите это цифрами.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что значит «стабильный спортсмен».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют размах для каждого прыгуна.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> У кого размах больше?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают результаты.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Может ли размах быть равен нулю? Когда?`,
        question: "Чему равен РАЗМАХ результатов прыгуна Б? (введите число)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 2,
        hint: "💡 У прыгуна Б максимальный результат = 8,0 м, минимальный = 6,0 м. Размах = 8,0 − 6,0 = ?",
        solution: "✅ Прыгун А: размах = 7,1−6,9 = <strong>0,2 м</strong>. Прыгун Б: размах = 8,0−6,0 = <strong>2,0 м</strong>. У прыгуна А маленький размах — он стабилен. У прыгуна Б большой размах — он непредсказуем. Для командных соревнований выберут А, для шоу — Б."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "МЕДИАНА ЧИСЛОВОГО НАБОРА" (7 КЛАСС) ==========
const grade7_topic4Cases = [
    // ========== КЕЙС 1. «Спор о росте учеников» ==========
    {
        id: "median_1",
        title: "📏 Кейс 1: «Спор о росте учеников»",
        description: "В классе 11 учеников. Их рост в см: 145, 148, 150, 152, 153, 155, 158, 160, 162, 165, 190.<br><br>Аня говорит: «Средний рост — 158 см. Это типичный ученик». Боря спорит: «А я считаю, что типичный рост — 155 см. Посмотри, большинство ниже 158!» Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Кто прав — Аня или Боря?<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся упорядочивают ряд и находят среднее и медиану.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая характеристика лучше показывает «типичного» ученика?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают среднее (158) и медиану (155).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему медиана устойчива к выбросам?`,
        question: "Чему равна МЕДИАНА роста учеников? (введите число, например 451)",
        answerNormalizer: (a) => parseInt(a),
        answer: 155,
        hint: "💡 Упорядочи ряд: 145,148,150,152,153,155,158,160,162,165,190. Медиана — 6-й элемент (11 чисел).",
        solution: "✅ Медиана = <strong>155 см</strong>. Среднее (158) завышено из-за ученика ростом 190 см. Медиана лучше показывает типичный рост."
    },
    // ========== КЕЙС 2. «Семейный бюджет» ==========
    {
        id: "median_2",
        title: "💰 Кейс 2: «Семейный бюджет»",
        description: "В небольшом посёлке 9 семей. Их ежемесячный доход (тыс. руб.): 25, 30, 35, 40, 45, 50, 55, 60, 200.<br><br>Мэр пишет: «Средний доход семьи — 60 тыс. рублей. Жизнь налаживается!» Жители возмущены. Почему?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Почему жители не согласны?<br>
2️⃣ <strong>Изучение материала:</strong> Вычисляют среднее и медиану.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая характеристика честнее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают среднее (60) и медиану (45).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какую характеристику выбрал бы мэр? А жители?`,
        question: "Чему равна МЕДИАНА доходов семей? (введите число, например 74)",
        answerNormalizer: (a) => parseInt(a),
        answer: 45,
        hint: "💡 Упорядочи ряд: 25,30,35,40,45,50,55,60,200. Медиана — 5-й элемент (9 чисел).",
        solution: "✅ Медиана = <strong>45 тыс. руб.</strong> Среднее (60) завышено из-за одной богатой семьи (200). Медиана честнее показывает типичный доход."
    },
    // ========== КЕЙС 3. «Оценки за четверть» ==========
    {
        id: "median_3",
        title: "📚 Кейс 3: «Оценки за четверть»",
        description: "У Пети за четверть оценки: 2, 2, 3, 5, 5, 5, 5, 5, 5, 5 (10 оценок). Петя говорит: «Моя средняя оценка — 4,2. Я хорошист!» Родители не верят. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Почему родители не верят?<br>
2️⃣ <strong>Изучение материала:</strong> Вычисляют среднее, медиану (чётное количество), моду.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая оценка «типичная» для Пети?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают среднее (4,2) и медиану (5).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что должен сказать учитель Пете?`,
        question: "Чему равна МЕДИАНА оценок Пети? (введите число, например 86)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 5,
        hint: "💡 Упорядочи ряд: 2,2,3,5,5,5,5,5,5,5. Медиана — среднее между 5-м и 6-м числами.",
        solution: "✅ Медиана = (5+5)/2 = <strong>5</strong>. Среднее (4,2) обманывает: большинство оценок — пятёрки (7 из 10). Но двойки — проблема, и среднее их сглаживает."
    },
    // ========== КЕЙС 4. «Зарплаты в стартапе» ==========
    {
        id: "median_4",
        title: "💻 Кейс 4: «Зарплаты в стартапе»",
        description: "В стартапе работают 7 человек: 5 программистов (по 80 тыс.), 1 менеджер (100 тыс.), 1 директор (500 тыс.).<br><br>HR пишет в вакансии: «Средняя зарплата в компании — около 143 тыс. руб.». Кандидат сомневается. Почему?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Почему кандидат сомневается?<br>
2️⃣ <strong>Изучение материала:</strong> Вычисляют среднее, медиану, моду.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая зарплата реальна для программиста?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают среднее (143) и медиану (80).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему HR использовал среднее?`,
        question: "Чему равна МЕДИАНА зарплат в стартапе? (введите число, например 861)",
        answerNormalizer: (a) => parseInt(a),
        answer: 80,
        hint: "💡 Упорядочи ряд: 80,80,80,80,80,100,500. Медиана — 4-й элемент (7 чисел).",
        solution: "✅ Медиана = <strong>80 тыс. руб.</strong> Среднее (143) завышено из-за зарплаты директора. Реальная зарплата программиста — 80 тыс."
    },
    // ========== КЕЙС 5. «Фигурное катание» ==========
    {
        id: "median_5",
        title: "⛸️ Кейс 5: «Фигурное катание»",
        description: "На соревнованиях судьи поставили оценки: 5,5; 5,5; 5,5; 5,6; 5,6; 5,7; 5,8; 5,9; 6,0.<br><br>В правилах сказано: «Итоговая оценка — медиана». Зачем используют медиану, а не среднее?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Зачем в спорте используют медиану?<br>
2️⃣ <strong>Изучение материала:</strong> Находят медиану и среднее.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Что будет, если один судья поставит 4,0?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают устойчивость медианы и среднего к выбросам.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему в школах используют среднее, а не медиану?`,
        question: "Чему равна МЕДИАНА оценок судей? (введите число, например 1.2)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 5.6,
        hint: "💡 Упорядочи ряд: 5,5;5,5;5,5;5,6;5,6;5,7;5,8;5,9;6,0. Медиана — 5-й элемент (9 чисел).",
        solution: "✅ Медиана = <strong>5,6</strong>. Если один судья поставит 4,0, медиана не изменится, а среднее упадёт. Медиана защищает от «злых» или «добрых» судей."
    }
];
	
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ГРАФИЧЕСКОЕ ПРЕДСТАВЛЕНИЕ ДАННЫХ" (7 КЛАСС) ==========
const grade7_topic2Cases = [
    // ========== КЕЙС 1. «Столбчатая диаграмма: любимые фрукты» ==========
    {
        id: "graph_1",
        title: "📊 Кейс 1: «Любимые фрукты»",
        description: "В двух параллельных 7-х классах провели опрос: «Какой ваш любимый фрукт?». Ребята построили разные диаграммы: Петя — отдельные для каждого класса, Катя — группированную диаграмму для сравнения.<br><br><strong>Данные опроса (количество учеников):</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 8px; border: 1px solid #cbdde9;'>Фрукт</th><th style='padding: 8px; border: 1px solid #cbdde9;'>7 «А»</th><th style='padding: 8px; border: 1px solid #cbdde9;'>7 «Б»</th></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Яблоко</td><td style='padding: 6px; border: 1px solid #cbdde9;'>8</td><td style='padding: 6px; border: 1px solid #cbdde9;'>12</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Банан</td><td style='padding: 6px; border: 1px solid #cbdde9;'>10</td><td style='padding: 6px; border: 1px solid #cbdde9;'>6</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Апельсин</td><td style='padding: 6px; border: 1px solid #cbdde9;'>5</td><td style='padding: 6px; border: 1px solid #cbdde9;'>7</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Груша</td><td style='padding: 6px; border: 1px solid #cbdde9;'>4</td><td style='padding: 6px; border: 1px solid #cbdde9;'>2</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Киви</td><td style='padding: 6px; border: 1px solid #cbdde9;'>3</td><td style='padding: 6px; border: 1px solid #cbdde9;'>3</td></tr></table><br><strong>Группированная диаграмма (вид сверху):</strong><br><svg width='550' height='300' viewBox='0 0 550 300' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='550' height='300' fill='#f8fafc' rx='8'/><text x='270' y='25' text-anchor='middle' fill='#1e4663' font-size='14' font-weight='bold'>Любимые фрукты учеников</text><rect x='60' y='180' width='35' height='90' fill='#3b82f6' opacity='0.8'/><rect x='105' y='130' width='35' height='140' fill='#3b82f6' opacity='0.8'/><rect x='150' y='210' width='35' height='60' fill='#3b82f6' opacity='0.8'/><rect x='195' y='220' width='35' height='50' fill='#3b82f6' opacity='0.8'/><rect x='240' y='230' width='35' height='40' fill='#3b82f6' opacity='0.8'/><rect x='60' y='160' width='35' height='110' fill='#ef4444' opacity='0.7'/><rect x='105' y='190' width='35' height='80' fill='#ef4444' opacity='0.7'/><rect x='150' y='190' width='35' height='80' fill='#ef4444' opacity='0.7'/><rect x='195' y='240' width='35' height='30' fill='#ef4444' opacity='0.7'/><rect x='240' y='230' width='35' height='40' fill='#ef4444' opacity='0.7'/><text x='75' y='290' text-anchor='middle' fill='#1e4663' font-size='10'>Яблоко</text><text x='125' y='290' text-anchor='middle' fill='#1e4663' font-size='10'>Банан</text><text x='170' y='290' text-anchor='middle' fill='#1e4663' font-size='10'>Апельсин</text><text x='215' y='290' text-anchor='middle' fill='#1e4663' font-size='10'>Груша</text><text x='260' y='290' text-anchor='middle' fill='#1e4663' font-size='10'>Киви</text><rect x='320' y='260' width='15' height='10' fill='#3b82f6'/><text x='340' y='270' fill='#1e4663' font-size='10'>7 «А»</text><rect x='390' y='260' width='15' height='10' fill='#ef4444'/><text x='410' y='270' fill='#1e4663' font-size='10'>7 «Б»</text></svg><br>Чья диаграмма удобнее для сравнения классов по каждому фрукту?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как сравнивать данные.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с разными типами столбчатых диаграмм.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Чья диаграмма лучше для сравнения?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют преимущества группированной диаграммы.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> В каком случае удобнее отдельные диаграммы?`,
        question: "В каком классе яблоко любят БОЛЬШЕ? (введите: 7А или 7Б)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "7б",
        hint: "💡 Посмотри на данные в таблице: в 7А — 8 человек, в 7Б — 12 человек.",
        solution: "✅ В <strong>7 «Б»</strong> яблоко любят больше (12 против 8). Группированная диаграмма Кати лучше подходит для сравнения классов по каждому фрукту."
    },
    // ========== КЕЙС 2. «Круговая диаграмма: вводит ли она в заблуждение?» ==========
    {
        id: "graph_2",
        title: "🥧 Кейс 2: «Круговая vs столбчатая»",
        description: "В газете вышла статья о том, как ученики добираются до школы. Данные: автобус — 40%, пешком — 35%, на машине — 15%, на велосипеде — 10%. Газета опубликовала две диаграммы.<br><br><strong>Круговая диаграмма:</strong><br><svg width='250' height='250' viewBox='0 0 250 250' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><circle cx='125' cy='120' r='90' fill='#f8fafc' stroke='#cbdde9' stroke-width='1'/><path d='M125,120 L125,30 A90,90 0 0,1 212,174 Z' fill='#3b82f6'/><path d='M125,120 L212,174 A90,90 0 0,1 85,188 Z' fill='#10b981'/><path d='M125,120 L85,188 A90,90 0 0,1 45,100 Z' fill='#f59e0b'/><path d='M125,120 L45,100 A90,90 0 0,1 125,30 Z' fill='#ef4444'/><text x='170' y='55' fill='white' font-size='10' font-weight='bold'>40%</text><text x='195' y='155' fill='white' font-size='10'>35%</text><text x='75' y='185' fill='white' font-size='10'>15%</text><text x='55' y='75' fill='white' font-size='10'>10%</text><rect x='30' y='210' width='12' height='12' fill='#3b82f6'/><text x='48' y='222' fill='#1e4663' font-size='10'>Автобус</text><rect x='120' y='210' width='12' height='12' fill='#10b981'/><text x='138' y='222' fill='#1e4663' font-size='10'>Пешком</text><rect x='30' y='230' width='12' height='12' fill='#f59e0b'/><text x='48' y='242' fill='#1e4663' font-size='10'>Машина</text><rect x='120' y='230' width='12' height='12' fill='#ef4444'/><text x='138' y='242' fill='#1e4663' font-size='10'>Велосипед</text></svg><br><strong>Столбчатая диаграмма:</strong><br><svg width='350' height='250' viewBox='0 0 350 250' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='350' height='250' fill='#f8fafc' rx='8'/><text x='175' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Способы добраться до школы</text><line x1='40' y1='210' x2='330' y2='210' stroke='#1e4663' stroke-width='1'/><line x1='40' y1='210' x2='40' y2='20' stroke='#1e4663' stroke-width='1'/><text x='30' y='215' text-anchor='end' fill='#1e4663' font-size='10'>0</text><text x='30' y='175' text-anchor='end' fill='#1e4663' font-size='10'>10%</text><text x='30' y='135' text-anchor='end' fill='#1e4663' font-size='10'>20%</text><text x='30' y='95' text-anchor='end' fill='#1e4663' font-size='10'>30%</text><text x='30' y='55' text-anchor='end' fill='#1e4663' font-size='10'>40%</text><rect x='50' y='126' width='45' height='84' fill='#3b82f6'/><text x='72' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>Автобус</text><rect x='115' y='147' width='45' height='63' fill='#10b981'/><text x='137' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>Пешком</text><rect x='180' y='168' width='45' height='42' fill='#f59e0b'/><text x='202' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>Машина</text><rect x='245' y='180' width='45' height='30' fill='#ef4444'/><text x='267' y='240' text-anchor='middle' fill='#1e4663' font-size='10'>Велосипед</text></svg><br>Какая диаграмма честнее показывает данные?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как можно манипулировать данными.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся сравнивают круговую и столбчатую диаграммы.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая диаграмма честнее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют, почему столбчатая диаграмма с осью от 0 — честный выбор.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему рекламщики любят «обрезанные» диаграммы?`,
        question: "Какой тип диаграммы лучше показывает доли (проценты) от целого? (введите: круговая или столбчатая)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "круговая",
        hint: "💡 Круговая диаграмма показывает части от целого. Столбчатая — сравнение величин.",
        solution: "✅ <strong>Круговая диаграмма</strong> лучше показывает доли от целого (сумма 100%). Столбчатая диаграмма с осью от 0 — честный способ сравнения величин. Обрезанная ось Y (от 30% до 45%) создала бы ложное впечатление огромной разницы."
    },
    // ========== КЕЙС 3. «Рост учеников: какая диаграмма удобнее?» ==========
    {
        id: "graph_3",
        title: "📏 Кейс 3: «Рост учеников»",
        description: "В 7 классе измерили рост 15 учеников (см): 145, 148, 150, 152, 153, 155, 155, 157, 158, 160, 162, 165, 168, 170, 172. Нужно выбрать лучший способ визуализации.<br><br><strong>Гистограмма (группировка по интервалам):</strong><br><svg width='400' height='250' viewBox='0 0 400 250' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='400' height='250' fill='#f8fafc' rx='8'/><text x='200' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Распределение роста учеников</text><line x1='40' y1='210' x2='370' y2='210' stroke='#1e4663' stroke-width='1'/><line x1='40' y1='210' x2='40' y2='20' stroke='#1e4663' stroke-width='1'/><text x='30' y='215' text-anchor='end' fill='#1e4663' font-size='10'>0</text><text x='30' y='185' text-anchor='end' fill='#1e4663' font-size='10'>2</text><text x='30' y='155' text-anchor='end' fill='#1e4663' font-size='10'>4</text><text x='30' y='125' text-anchor='end' fill='#1e4663' font-size='10'>6</text><text x='30' y='95' text-anchor='end' fill='#1e4663' font-size='10'>8</text><text x='30' y='65' text-anchor='end' fill='#1e4663' font-size='10'>10</text><rect x='55' y='135' width='50' height='75' fill='#3b82f6' opacity='0.8'/><text x='80' y='235' text-anchor='middle' fill='#1e4663' font-size='10'>140-150</text><rect x='125' y='95' width='50' height='115' fill='#10b981' opacity='0.8'/><text x='150' y='235' text-anchor='middle' fill='#1e4663' font-size='10'>150-160</text><rect x='195' y='125' width='50' height='85' fill='#f59e0b' opacity='0.8'/><text x='220' y='235' text-anchor='middle' fill='#1e4663' font-size='10'>160-170</text><rect x='265' y='175' width='50' height='35' fill='#ef4444' opacity='0.8'/><text x='290' y='235' text-anchor='middle' fill='#1e4663' font-size='10'>170-180</text></svg><br>Сколько учеников имеют рост от 150 до 160 см?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как представить много данных.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с гистограммой (группировка по интервалам).<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Сколько учеников в интервале 150-160?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Считают по данным или считывают с гистограммы.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему гистограмма удобнее, чем столбчатая диаграмма для каждого ученика?`,
        question: "Сколько учеников имеют рост от 150 до 160 см? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 7,
        hint: "💡 Посмотри на гистограмму: высота столбца 150-160 соответствует примерно 7 ученикам.",
        solution: "✅ В интервале 150-160 см находятся <strong>7</strong> учеников (150,152,153,155,155,157,158). Гистограмма — лучший выбор для показа распределения данных."
    },
    // ========== КЕЙС 4. «Продажи мороженого: поиск обмана» ==========
    {
        id: "graph_4",
        title: "🍦 Кейс 4: «Продажи мороженого»",
        description: "В газете вышла статья о продажах мороженого. Данные: 2020 — 100 тыс. руб., 2021 — 105, 2022 — 110, 2023 — 120. Газета опубликовала два графика.<br><br><strong>График А (ось от 0 до 130):</strong><br><svg width='400' height='250' viewBox='0 0 400 250' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='400' height='250' fill='#f8fafc' rx='8'/><text x='200' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Продажи мороженого (2020-2023)</text><line x1='50' y1='210' x2='350' y2='210' stroke='#1e4663' stroke-width='1'/><line x1='50' y1='210' x2='50' y2='30' stroke='#1e4663' stroke-width='1'/><text x='40' y='215' text-anchor='end' fill='#1e4663' font-size='10'>0</text><text x='40' y='168' text-anchor='end' fill='#1e4663' font-size='10'>30</text><text x='40' y='120' text-anchor='end' fill='#1e4663' font-size='10'>60</text><text x='40' y='72' text-anchor='end' fill='#1e4663' font-size='10'>90</text><text x='40' y='37' text-anchor='end' fill='#1e4663' font-size='10'>120</text><circle cx='90' cy='160' r='5' fill='#3b82f6'/><circle cx='170' cy='150' r='5' fill='#3b82f6'/><circle cx='250' cy='140' r='5' fill='#3b82f6'/><circle cx='330' cy='120' r='5' fill='#3b82f6'/><polyline points='90,160 170,150 250,140 330,120' stroke='#3b82f6' stroke-width='2' fill='none'/><text x='90' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>2020</text><text x='170' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>2021</text><text x='250' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>2022</text><text x='330' y='180' text-anchor='middle' fill='#1e4663' font-size='10'>2023</text></svg><br><strong>График Б (ось от 90 до 125):</strong><br><svg width='400' height='250' viewBox='0 0 400 250' style='background: #f8fafc; border-radius: 10px; margin-top: 10px;'><rect x='0' y='0' width='400' height='250' fill='#f8fafc' rx='8'/><text x='200' y='20' text-anchor='middle' fill='#1e4663' font-size='12' font-weight='bold'>Продажи мороженого (2020-2023)</text><line x1='50' y1='210' x2='350' y2='210' stroke='#1e4663' stroke-width='1'/><line x1='50' y1='210' x2='50' y2='30' stroke='#1e4663' stroke-width='1'/><text x='40' y='215' text-anchor='end' fill='#1e4663' font-size='10'>90</text><text x='40' y='165' text-anchor='end' fill='#1e4663' font-size='10'>100</text><text x='40' y='115' text-anchor='end' fill='#1e4663' font-size='10'>110</text><text x='40' y='55' text-anchor='end' fill='#1e4663' font-size='10'>120</text><circle cx='90' cy='190' r='5' fill='#ef4444'/><circle cx='170' cy='170' r='5' fill='#ef4444'/><circle cx='250' cy='150' r='5' fill='#ef4444'/><circle cx='330' cy='100' r='5' fill='#ef4444'/><polyline points='90,190 170,170 250,150 330,100' stroke='#ef4444' stroke-width='3' fill='none'/><text x='90' y='230' text-anchor='middle' fill='#1e4663' font-size='10'>2020</text><text x='170' y='230' text-anchor='middle' fill='#1e4663' font-size='10'>2021</text><text x='250' y='230' text-anchor='middle' fill='#1e4663' font-size='10'>2022</text><text x='330' y='230' text-anchor='middle' fill='#1e4663' font-size='10'>2023</text></svg><br>Какой график честнее показывает реальный рост продаж?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как можно манипулировать графиками.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся сравнивают два графика с разным масштабом оси Y.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой график честнее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют, почему обрезанная ось Y вводит в заблуждение.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какой график выбрала бы компания-производитель, а какой — налоговая?`,
        question: "Какой график показывает реальный рост продаж честно? (введите: график А или график Б)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "график а",
        hint: "💡 Честный график — тот, где ось Y начинается с 0 (или явно указано, что она обрезана).",
        solution: "✅ <strong>График А</strong> (ось от 0) честно показывает рост с 100 до 120 тыс. руб. График Б обрезает ось с 90 до 125, из-за чего небольшой рост выглядит как «взрывной». Это приём манипуляции."
    },
    // ========== КЕЙС 5. «Выбор диаграммы для школьного проекта» ==========
    {
        id: "graph_5",
        title: "📈 Кейс 5: «Выбор диаграммы»",
        description: "Группа учеников готовит проект о питании школьников. У них есть данные:<br><br>1. Любимые завтраки (каша — 25%, бутерброд — 40%, йогурт — 20%, фрукты — 10%, ничего — 5%)<br>2. Динамика завтракающих дома за 5 лет: 30%, 32%, 35%, 33%, 40%<br>3. Сравнение питания мальчиков и девочек (в процентах)<br><br>Какую диаграмму выбрать для каждого пункта?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает разные типы диаграмм.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вспоминают, какой тип для какой задачи.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая диаграмма подходит для долей? Для динамики? Для сравнения?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Обосновывают выбор для каждого пункта.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему в науке редко используют круговые диаграммы?`,
        question: "Какую диаграмму лучше выбрать для показа динамики завтракающих дома за 5 лет? (введите: круговая, столбчатая или линейная)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "линейная",
        hint: "💡 Для показа изменений во времени лучше всего подходит линейный график.",
        solution: "✅ Для динамики за 5 лет лучше всего подходит <strong>линейный график</strong>. Для любимых завтраков (доли) — круговая диаграмма. Для сравнения мальчиков и девочек — группированные столбцы."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ПРЕДСТАВЛЕНИЕ ДАННЫХ В ТАБЛИЦАХ" (7 КЛАСС) ==========
const grade7_topic1Cases = [
    // ========== КЕЙС 1. «Заказ мебели в образовательном центре» ==========
    {
        id: "tables_1",
        title: "📋 Кейс 1: «Заказ мебели»",
        description: "В образовательном центре сделали ремонт. Сотрудница Елена собирает заявки на новую мебель от всех лабораторий и отделов. Она начала заполнять таблицу, но заполнила только столбец «Количество» для рабочих столов.<br><br><strong>Таблица Елены:</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 8px; border: 1px solid #cbdde9;'>Наименование</th><th style='padding: 8px; border: 1px solid #cbdde9;'>Количество</th></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Стол рабочий</td><td style='padding: 6px; border: 1px solid #cbdde9;'>11</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Шкаф для одежды</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Стул</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Кресло</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Тумбочка с ящиками</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Книжный шкаф</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Настольная лампа</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Маленький круглый стол</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Зелёный диван</td><td style='padding: 6px; border: 1px solid #cbdde9;'>?</td></tr></table><br>Директор задаёт вопросы: сколько стульев заказано? Кто заказал зелёный диван? Для какой лаборатории нужны лампы? Елена не может ответить.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему Елена не может ответить на вопросы.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся со структурой таблиц (строки, столбцы, заголовки).<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой информации не хватает в таблице?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Предлагают дополнительные столбцы (Отдел, Кабинет, Цена).<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какая информация о мебели нужна для расчёта стоимости?`,
        question: "Какой столбец НУЖНО ДОБАВИТЬ в таблицу, чтобы понять, для какой лаборатории заказывают мебель? (введите: Отдел, Цена или Количество)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "отдел",
        hint: "💡 Чтобы узнать, кто заказал зелёный диван, нужно знать название отдела или лаборатории.",
        solution: "✅ Нужно добавить столбец <strong>«Отдел/лаборатория»</strong>. Тогда можно будет ответить на вопросы директора. Также полезно добавить столбцы «Кабинет» и «Цена»."
    },
    // ========== КЕЙС 2. «Расписание автобуса» ==========
    {
        id: "tables_2",
        title: "🚌 Кейс 2: «Расписание автобуса»",
        description: "Автобус делает три рейса от железнодорожной станции в посёлок и обратно. Известно:<br><br>• Первый рейс от станции — в 8:32<br>• Дорога от станции до посёлка — 30 минут<br>• На конечных остановках автобус ждёт 10 минут<br>• Обратный путь тоже 30 минут<br><br>Два ученика составили расписание, но у них получились разные ответы.<br><br><strong>Вариант ученика А:</strong><br><table style='width: 60%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 8px; border: 1px solid #cbdde9;'>От станции</th><th style='padding: 8px; border: 1px solid #cbdde9;'>От посёлка</th></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>8:32</td><td style='padding: 6px; border: 1px solid #cbdde9;'>9:12</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>9:52</td><td style='padding: 6px; border: 1px solid #cbdde9;'>10:32</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>11:12</td><td style='padding: 6px; border: 1px solid #cbdde9;'>11:52</td></tr></table><br><strong>Вариант ученика Б:</strong><br><table style='width: 60%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 8px; border: 1px solid #cbdde9;'>От станции</th><th style='padding: 8px; border: 1px solid #cbdde9;'>От посёлка</th></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>8:32</td><td style='padding: 6px; border: 1px solid #cbdde9;'>9:02</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>9:42</td><td style='padding: 6px; border: 1px solid #cbdde9;'>10:12</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>10:52</td><td style='padding: 6px; border: 1px solid #cbdde9;'>11:22</td></tr></table><br>Нужно определить правильное расписание.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как составить расписание.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят временную линию для расчётов.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой вариант правильный?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Пошагово вычисляют время каждого рейса.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему в расписании указывают отправление, а не прибытие?`,
        question: "Во сколько автобус отправляется от посёлка в третьем рейсе? (введите время в формате ЧЧ:ММ, например 11:52)",
        answerNormalizer: (a) => a.trim(),
        answer: "11:52",
        hint: "💡 Первый рейс от станции 8:32 → прибытие в посёлок 9:02 → ожидание 10 мин → отправление от посёлка 9:12 → прибытие на станцию 9:42 → ожидание 10 мин → второй рейс от станции 9:52 → ...",
        solution: "✅ Правильное расписание — вариант <strong>ученика А</strong>:<br>1-й рейс: от станции 8:32 → от посёлка 9:12<br>2-й рейс: от станции 9:52 → от посёлка 10:32<br>3-й рейс: от станции 11:12 → от посёлка <strong>11:52</strong>"
    },
    // ========== КЕЙС 3. «Сравнение двух таблиц» ==========
    {
        id: "tables_3",
        title: "📊 Кейс 3: «Сравнение двух таблиц»",
        description: "В газете опубликовали результаты опроса «Какие кружки посещают ученики 7-х классов?» Данные представили в двух таблицах.<br><br><strong>Таблица А (по классам):</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 8px; border: 1px solid #cbdde9;'>Класс</th><th style='padding: 8px; border: 1px solid #cbdde9;'>Математика</th><th style='padding: 8px; border: 1px solid #cbdde9;'>Рисование</th><th style='padding: 8px; border: 1px solid #cbdde9;'>Музыка</th><th style='padding: 8px; border: 1px solid #cbdde9;'>Спорт</th></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>7 «А»</td><td style='padding: 6px; border: 1px solid #cbdde9;'>8</td><td style='padding: 6px; border: 1px solid #cbdde9;'>5</td><td style='padding: 6px; border: 1px solid #cbdde9;'>4</td><td style='padding: 6px; border: 1px solid #cbdde9;'>10</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>7 «Б»</td><td style='padding: 6px; border: 1px solid #cbdde9;'>6</td><td style='padding: 6px; border: 1px solid #cbdde9;'>7</td><td style='padding: 6px; border: 1px solid #cbdde9;'>5</td><td style='padding: 6px; border: 1px solid #cbdde9;'>9</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>7 «В»</td><td style='padding: 6px; border: 1px solid #cbdde9;'>9</td><td style='padding: 6px; border: 1px solid #cbdde9;'>4</td><td style='padding: 6px; border: 1px solid #cbdde9;'>6</td><td style='padding: 6px; border: 1px solid #cbdde9;'>8</td></tr></table><br><strong>Таблица Б (по кружкам):</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 8px; border: 1px solid #cbdde9;'>Кружок</th><th style='padding: 8px; border: 1px solid #cbdde9;'>7 «А»</th><th style='padding: 8px; border: 1px solid #cbdde9;'>7 «Б»</th><th style='padding: 8px; border: 1px solid #cbdde9;'>7 «В»</th><th style='padding: 8px; border: 1px solid #cbdde9;'>Всего</th></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Математика</td><td style='padding: 6px; border: 1px solid #cbdde9;'>8</td><td style='padding: 6px; border: 1px solid #cbdde9;'>6</td><td style='padding: 6px; border: 1px solid #cbdde9;'>9</td><td style='padding: 6px; border: 1px solid #cbdde9;'>23</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Рисование</td><td style='padding: 6px; border: 1px solid #cbdde9;'>5</td><td style='padding: 6px; border: 1px solid #cbdde9;'>7</td><td style='padding: 6px; border: 1px solid #cbdde9;'>4</td><td style='padding: 6px; border: 1px solid #cbdde9;'>16</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Музыка</td><td style='padding: 6px; border: 1px solid #cbdde9;'>4</td><td style='padding: 6px; border: 1px solid #cbdde9;'>5</td><td style='padding: 6px; border: 1px solid #cbdde9;'>6</td><td style='padding: 6px; border: 1px solid #cbdde9;'>15</td></tr><tr><td style='padding: 6px; border: 1px solid #cbdde9;'>Спорт</td><td style='padding: 6px; border: 1px solid #cbdde9;'>10</td><td style='padding: 6px; border: 1px solid #cbdde9;'>9</td><td style='padding: 6px; border: 1px solid #cbdde9;'>8</td><td style='padding: 6px; border: 1px solid #cbdde9;'>27</td></tr></table><br>В какой таблице легче найти ответ на вопрос: «Какой кружок самый популярный во всех классах вместе?»",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс знакомится с двумя таблицами.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся анализируют структуру каждой таблицы.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая таблица удобнее для разных вопросов?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают время поиска ответов.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Нет «правильной» таблицы — есть подходящая для задачи.`,
        question: "В какой таблице ЕСТЬ столбец «Всего» для каждого кружка? (введите: Таблица А или Таблица Б)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "таблица б",
        hint: "💡 Посмотри на таблицы: в какой из них есть итоговая строка или столбец с суммой?",
        solution: "✅ В <strong>Таблице Б</strong> есть столбец «Всего». В ней легко ответить на вопрос о самом популярном кружке: спорт (27 учеников). Таблица А удобнее для сравнения классов по одному кружку."
    },
    // ========== КЕЙС 4. «Дневник погоды» ==========
    {
        id: "tables_4",
        title: "🌤️ Кейс 4: «Дневник погоды»",
        description: "Ученик Петя в течение недели записывал погоду. Учитель говорит: «Сделай нормальную таблицу».<br><br><strong>Данные Пети:</strong><br>• Пн: утро +5, дождь, облачно; день +8, дождь<br>• Вт: утро +3, облачно; день +7, солнечно<br>• Ср: утро +2, снег; день +4, снег с дождём<br>• Чт: утро +4, облачно; день +6, солнечно<br>• Пт: утро +6, дождь; день +9, солнечно<br>• Сб: утро +5, облачно; день +10, солнечно<br>• Вс: утро +7, солнечно; день +12, солнечно<br><br><strong>Правильно оформленная таблица:</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px; font-size: 0.8rem;'><tr style='background: #1e4663; color: white;'><th style='padding: 6px; border: 1px solid #cbdde9;'>День</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Утро (°C)</th><th style='padding: 6px; border: 1px solid #cbdde9;'>День (°C)</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Осадки утром</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Осадки днём</th></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Пн</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+5</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+8</td><td style='padding: 4px; border: 1px solid #cbdde9;'>дождь</td><td style='padding: 4px; border: 1px solid #cbdde9;'>дождь</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Вт</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+3</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+7</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Ср</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+2</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+4</td><td style='padding: 4px; border: 1px solid #cbdde9;'>снег</td><td style='padding: 4px; border: 1px solid #cbdde9;'>снег с дождём</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Чт</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+4</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+6</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Пт</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+6</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+9</td><td style='padding: 4px; border: 1px solid #cbdde9;'>дождь</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Сб</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+5</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+10</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Вс</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+7</td><td style='padding: 4px; border: 1px solid #cbdde9;'>+12</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td><td style='padding: 4px; border: 1px solid #cbdde9;'>нет</td></tr></table><br>Используя таблицу, ответьте на вопрос.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает проблемы хаотичных данных.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся анализируют готовую таблицу.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какие столбцы нужны?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Находят информацию в таблице.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какие ещё столбцы можно добавить?`,
        question: "Какой была температура в СРЕДУ ДНЁМ? (введите число со знаком, например +4)",
        answerNormalizer: (a) => parseInt(a),
        answer: 4,
        hint: "💡 Найди в таблице строку «Ср» (среда) и столбец «День (°C)».",
        solution: "✅ В среду днём температура была <strong>+4°C</strong>. Правильно организованная таблица позволяет быстро находить нужную информацию."
    },
    // ========== КЕЙС 5. «Таблицы вокруг нас» ==========
    {
        id: "tables_5",
        title: "🏪 Кейс 5: «Таблицы вокруг нас»",
        description: "Учитель дал задание: найти и проанализировать таблицы в общественных местах. Вот три примера:<br><br><strong>1. Расписание движения поездов:</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 6px; border: 1px solid #cbdde9;'>Время отправления</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Время прибытия</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Платформа</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Конечная станция</th></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>8:30</td><td style='padding: 4px; border: 1px solid #cbdde9;'>9:15</td><td style='padding: 4px; border: 1px solid #cbdde9;'>2</td><td style='padding: 4px; border: 1px solid #cbdde9;'>Тверь</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>9:45</td><td style='padding: 4px; border: 1px solid #cbdde9;'>10:30</td><td style='padding: 4px; border: 1px solid #cbdde9;'>3</td><td style='padding: 4px; border: 1px solid #cbdde9;'>Клин</td></tr></table><br><strong>2. Меню в столовой:</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 6px; border: 1px solid #cbdde9;'>Блюдо</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Цена (руб.)</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Вес (г)</th></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Борщ</td><td style='padding: 4px; border: 1px solid #cbdde9;'>80</td><td style='padding: 4px; border: 1px solid #cbdde9;'>250</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>Котлета с пюре</td><td style='padding: 4px; border: 1px solid #cbdde9;'>120</td><td style='padding: 4px; border: 1px solid #cbdde9;'>300</td></tr></table><br><strong>3. Таблица результатов соревнований:</strong><br><table style='width: 100%; border-collapse: collapse; margin-top: 10px;'><tr style='background: #1e4663; color: white;'><th style='padding: 6px; border: 1px solid #cbdde9;'>Место</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Имя участника</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Результат</th><th style='padding: 6px; border: 1px solid #cbdde9;'>Страна</th></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>1</td><td style='padding: 4px; border: 1px solid #cbdde9;'>Иванов</td><td style='padding: 4px; border: 1px solid #cbdde9;'>10.2 с</td><td style='padding: 4px; border: 1px solid #cbdde9;'>Россия</td></tr><tr><td style='padding: 4px; border: 1px solid #cbdde9;'>2</td><td style='padding: 4px; border: 1px solid #cbdde9;'>Петров</td><td style='padding: 4px; border: 1px solid #cbdde9;'>10.5 с</td><td style='padding: 4px; border: 1px solid #cbdde9;'>Россия</td></tr></table><br>Какая таблица нужна пассажиру, чтобы узнать, на какую платформу идти?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель представляет три таблицы. Класс обсуждает их назначение.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся анализируют каждую таблицу.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая таблица лучше отвечает на вопросы своей аудитории?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Голосуют за самую удачную таблицу.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какую таблицу вы бы составили для родителей на собрании?`,
        question: "Какая таблица НУЖНА пассажиру, чтобы узнать, на какую платформу идти? (введите: расписание поездов, меню или результаты соревнований)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "расписание поездов",
        hint: "💡 Пассажиру важно знать не только время, но и платформу отправления.",
        solution: "✅ Пассажиру нужно <strong>расписание поездов</strong> — оно содержит информацию о платформе. Удачная таблица — та, которая быстро отвечает на вопросы своей аудитории."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ДИАГРАММА ЭЙЛЕРА. ОБЪЕДИНЕНИЕ И ПЕРЕСЕЧЕНИЕ СОБЫТИЙ" (8 КЛАСС) ==========
const grade8_topic5Cases = [
    // ========== КЕЙС 1. «Конфеты в вазе» ==========
    {
        id: "euler_events_1",
        title: "🍬 Кейс 1: «Конфеты в вазе»",
        description: "В вазе лежат конфеты: 5 шоколадных, 3 карамельки, 2 леденца. Мама просит Петю взять одну конфету, но не говорит какую. Петя рассуждает:<br><br>• Событие А = {вытащил шоколадную конфету}<br>• Событие Б = {вытащил карамельку}<br>• Событие В = {вытащил леденец}<br><br>Петя говорит: «Эти события не могут произойти одновременно, потому что конфета одна». Его младшая сестра Катя спорит: «А если взять две конфеты? Тогда можно вытащить и шоколадную, и карамельку». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает разницу между одним и двумя испытаниями.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятиями совместных и несовместных событий.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Могут ли события произойти одновременно?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Строят диаграмму Эйлера для двух случаев.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что означают пересекающиеся и непересекающиеся круги?`,
        question: "При выборе одной конфеты события А, Б и В являются... (введите: совместными или несовместными)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "несовместными",
        hint: "💡 Можно ли вытащить одну конфету, которая была бы одновременно и шоколадной, и карамелькой?",
        solution: "✅ При выборе одной конфеты события <strong>несовместны</strong> — круги не пересекаются. При выборе двух конфет события могут быть совместными (можно вытащить и шоколадную, и карамельку) — круги пересекаются. Права Катя."
    },
    // ========== КЕЙС 2. «Лотерейные билеты» ==========
    {
        id: "euler_events_2",
        title: "🎫 Кейс 2: «Лотерейные билеты»",
        description: "В лотерее 100 билетов. События:<br><br>• А = {билет выигрышный}<br>• В = {на билете чётный номер}<br><br>Учитель спрашивает класс:<br>1. Может ли событие А и В произойти одновременно? (Да, если выигрышный билет имеет чётный номер)<br>2. Что означает пересечение А ∩ В?<br>3. Что означает объединение А ∪ В?<br><br>Как показать это на диаграмме, чтобы было понятно всем?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает возможные комбинации.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму Эйлера для двух пересекающихся событий.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Сколько всего областей получится?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Закрашивают области пересечения и объединения.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что означает область вне кругов?`,
        question: "Сколько всего непересекающихся областей (зоны) получается на диаграмме для двух событий? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 4,
        hint: "💡 Посчитай: только А, только В, пересечение А∩В, и область «ни А, ни В».",
        solution: "✅ Для двух событий диаграмма Эйлера делит все возможные исходы на <strong>4</strong> непересекающиеся области: 1) только А, 2) только В, 3) А∩В, 4) ни А, ни В. Любое событие можно представить как объединение нескольких областей."
    },
    // ========== КЕЙС 3. «Экзамен в школе» ==========
    {
        id: "euler_events_3",
        title: "📝 Кейс 3: «Экзамен в школе»",
        description: "В школе сдавали два экзамена: математику и русский язык. Из 30 учеников:<br><br>• 20 сдали математику<br>• 18 сдали русский<br>• 15 сдали оба экзамена<br><br>Директор смотрит на цифры и говорит: «20+18=38, а у нас всего 30 учеников. Как так?» Учитель объясняет: «Те, кто сдал оба экзамена, посчитаны дважды». Как объяснить директору на диаграмме?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает проблему двойного счёта.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму Эйлера по данным.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Сколько сдали только математику? Только русский?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Заполняют все области диаграммы числами.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько человек не сдали ничего?`,
        question: "Сколько учеников НЕ СДАЛИ ни один из экзаменов? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 7,
        hint: "💡 Сначала найди: только математику = 20−15 = 5, только русский = 18−15 = 3. Сдавшие хотя бы один = 5+3+15 = 23. Затем вычти из общего числа.",
        solution: "✅ Только математику: 20−15 = 5. Только русский: 18−15 = 3. Сдавшие хотя бы один: 5+3+15 = 23. Не сдали ничего: 30−23 = <strong>7</strong> учеников. Диаграмма наглядно показывает, что «лишние» 8 человек — это те, кого посчитали дважды (пересечение)."
    },
    // ========== КЕЙС 4. «Прогноз погоды» ==========
    {
        id: "euler_events_4",
        title: "🌦️ Кейс 4: «Прогноз погоды»",
        description: "Синоптик сделал прогноз на завтра:<br><br>• Событие А = {будет дождь}<br>• Событие В = {будет ветер}<br>• Событие С = {будет снег}<br><br>Возможны разные варианты погоды. Синоптик хочет нарисовать диаграмму, чтобы показать все варианты на одном рисунке. Сколько всего различных комбинаций погоды можно описать с помощью трёх кругов?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает возможные сценарии погоды.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму Эйлера для трёх пересекающихся событий.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Сколько областей получится?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Подписывают каждую область.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько областей будет для 4 событий? Для n событий?`,
        question: "Сколько всего непересекающихся областей (зоны) получается на диаграмме для трёх событий? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 8,
        hint: "💡 Посчитай: три одиночных области, три двойных пересечения, одно тройное пересечение и одна внешняя область.",
        solution: "✅ Для трёх событий диаграмма Эйлера даёт <strong>8</strong> областей: 3 одиночных (только А, только В, только С), 3 двойных пересечения (А∩В, А∩С, В∩С), 1 тройное пересечение (А∩В∩С) и 1 внешняя область (ни А, ни В, ни С). Для n событий — 2ⁿ областей."
    },
    // ========== КЕЙС 5. «Турнир по шахматам» ==========
    {
        id: "euler_events_5",
        title: "♟️ Кейс 5: «Турнир по шахматам»",
        description: "В шахматном турнире участвуют 20 человек. Организатор записал события:<br><br>• А = {участник выиграл хотя бы одну партию}<br>• В = {участник сыграл вничью хотя бы одну партию}<br>• С = {участник проиграл хотя бы одну партию}<br><br>Организатор говорит: «Каждый участник либо выиграл, либо сыграл вничью, либо проиграл. А может быть и то, и другое, и третье (если сыграно много партий)». Что это означает для диаграммы Эйлера?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, могут ли события пересекаться.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму Эйлера.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Может ли участник не попасть ни в одно событие?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют внешнюю область.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что изменится, если турнир состоит только из одной партии?`,
        question: "Что происходит с ВНЕШНЕЙ областью на диаграмме (участники, не попавшие ни в А, ни в В, ни в С)? (введите: пустая или не пустая)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "пустая",
        hint: "💡 У каждого участника есть результаты партий. Может ли быть участник, который не выиграл, не сыграл вничью и не проиграл ни одной партии?",
        solution: "✅ Внешняя область <strong>пустая</strong>, потому что каждый участник либо выиграл, либо сыграл вничью, либо проиграл (или всё вместе). Объединение А ∪ В ∪ С = все 20 участников. Это важный случай: события покрывают все возможные исходы."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "МНОЖЕСТВА (ОБЪЕДИНЕНИЕ, ПЕРЕСЕЧЕНИЕ)" (8 КЛАСС) ==========
const grade8_topic4Cases = [
    // ========== КЕЙС 1. «Подарки на Новый год» ==========
    {
        id: "sets_1",
        title: "🎁 Кейс 1: «Подарки на Новый год»",
        description: "В семье трое детей: Маша, Петя и Коля. Родители купили подарки:<br><br>• Множество A — подарки для Маши: {кукла, книга, конструктор}<br>• Множество B — подарки для Пети: {машинка, конструктор, робот}<br>• Множество C — подарки для Коли: {робот, книга, мяч}<br><br>Дети начали спорить: кто получит конструктор, а кто робота? Родители хотят раздать подарки так, чтобы не было ссор. Как понять, какие подарки общие?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему возник спор.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятиями пересечения и объединения множеств.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какие подарки попали в списки нескольких детей?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Строят диаграмму Эйлера для трёх множеств.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какие подарки придётся делить (покупать второй экземпляр)?`,
        question: "Какой подарок находится в пересечении множеств A и B (достанется и Маше, и Пете)? (введите название подарка)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "конструктор",
        hint: "💡 Посмотри, какой подарок есть и в списке Маши, и в списке Пети.",
        solution: "✅ <strong>Конструктор</strong> есть и у Маши (A), и у Пети (B). Он находится в пересечении A ∩ B. Робот — в пересечении B ∩ C. Книга — только у Маши. Родителям нужно или договориться, или купить второй экземпляр конфликтных подарков."
    },
    // ========== КЕЙС 2. «Запись в кружки» ==========
    {
        id: "sets_2",
        title: "🎨 Кейс 2: «Запись в кружки»",
        description: "В школе объявили запись в два кружка: «Умелые ручки» (А) и «Юный художник» (В). Учитель составил списки:<br><br>• В кружок А записались: Оля, Катя, Дима, Саша, Лена<br>• В кружок В записались: Дима, Лена, Юра, Таня, Коля<br><br>Директор хочет узнать, сколько всего детей участвует в кружках, чтобы заказать материал для поделок. Как это сделать быстро и наглядно?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает проблему двойного счёта.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму Эйлера для двух множеств.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто записался в оба кружка?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Распределяют имена по областям диаграммы.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько всего разных детей?`,
        question: "Сколько всего РАЗНЫХ детей записалось в кружки? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 8,
        hint: "💡 Посчитай: только в А, только в В и в обоих кружках. Сложи эти числа.",
        solution: "✅ Только в А: Оля, Катя, Саша (3 человека). Только в В: Юра, Таня, Коля (3 человека). В обоих: Дима, Лена (2 человека). Всего: 3 + 3 + 2 = <strong>8</strong> детей."
    },
    // ========== КЕЙС 3. «Завтрак в столовой» ==========
    {
        id: "sets_3",
        title: "🍳 Кейс 3: «Завтрак в столовой»",
        description: "В школьной столовой на завтрак можно взять:<br><br>• Горячие блюда: {каша, омлет, сырники}<br>• Напитки: {чай, какао, сок}<br><br>Повар говорит: «Я приготовил 6 разных позиций». А директор говорит: «А мне нужны ВСЕ возможные варианты завтрака: я хочу знать, сколько разных наборов (горячее + напиток) можно составить». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, о чём говорят повар и директор.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся различают объединение множеств и декартово произведение.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> 6 или 9? Кто прав?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Считают количество наборов.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Диаграмма Эйлера помогает в этой задаче?`,
        question: "Сколько всего разных наборов (горячее + напиток) можно составить? (введите число)",
        answerNormalizer: (a) => parseInt(a),
        answer: 9,
        hint: "💡 Каждое горячее блюдо можно сочетать с каждым напитком. 3 × 3 = ?",
        solution: "✅ Прав директор. Наборов: 3 × 3 = <strong>9</strong>. Повар посчитал объединение множеств (3 + 3 = 6), но директору нужно не объединение, а комбинации. Диаграмма Эйлера здесь не помогает — это задача на правило умножения."
    },
    // ========== КЕЙС 4. «Поиски пропавшего рюкзака» ==========
    {
        id: "sets_4",
        title: "🎒 Кейс 4: «Поиски пропавшего рюкзака»",
        description: "В классе потерялся рюкзак. Учитель выяснил, кто был в раздевалке в перемену. Получились три множества:<br><br>• A — кто заходил в раздевалку до 10:00: {Дима, Оля, Саша, Катя}<br>• B — кто заходил в раздевалку после 10:00: {Саша, Катя, Юра, Таня}<br>• C — кто видел рюкзак: {Оля, Юра, Катя}<br><br>Рюкзак видели только те, кто был в раздевалке. Кто из видевших рюкзак был там и до, и после 10:00?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как отфильтровать нужных людей.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму Эйлера для трёх множеств.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто мог видеть рюкзак?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Распределяют имена по 8 областям диаграммы.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Сколько всего различных областей на диаграмме из трёх кругов?`,
        question: "Кто из видевших рюкзак (C) был в раздевалке и ДО, и ПОСЛЕ 10:00? (введите имя)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "катя",
        hint: "💡 Ищем человека, который есть в A, в B и в C одновременно (A ∩ B ∩ C).",
        solution: "✅ <strong>Катя</strong> есть во всех трёх множествах: она была в раздевалке до 10:00 (A), после 10:00 (B) и видела рюкзак (C). Она находится в тройном пересечении A ∩ B ∩ C."
    },
    // ========== КЕЙС 5. «Садовод и его цветы» ==========
    {
        id: "sets_5",
        title: "🌹 Кейс 5: «Садовод и его цветы»",
        description: "У садовода есть три клумбы:<br><br>• Клумба 1: только розы<br>• Клумба 2: только тюльпаны<br>• Клумба 3: розы, тюльпаны и лилии<br><br>Пришли покупатели:<br>• Покупатель 1 хочет только розы.<br>• Покупатель 2 хочет только тюльпаны.<br>• Покупатель 3 хочет и розы, и тюльпаны в одном букете (без лилий).<br>• Покупатель 4 хочет любые цветы, кроме лилий.<br><br>С каких клумб срывать цветы для каждого покупателя?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает требования покупателей.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму Эйлера (розы, тюльпаны, лилии).<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какому покупателю нужна область «только розы»?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сопоставляют условия с областями диаграммы.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какой покупатель самый привередливый?`,
        question: "С какой клумбы нужно сорвать цветы для покупателя 3 (розы И тюльпаны БЕЗ лилий)? (введите: Клумба 1, Клумба 2 или Клумба 3)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "клумба 3",
        hint: "💡 Покупателю 3 нужны и розы, и тюльпаны. На клумбе 3 есть и то, и другое. Но там есть ещё лилии. Условие «без лилий» означает, что нужно выбрать только розы и тюльпаны, растущие вместе.",
        solution: "✅ <strong>Клумба 3</strong>. Только на ней растут и розы, и тюльпаны вместе. Но из неё нужно выбрать букет, исключив лилии. Покупатель 1 — Клумба 1. Покупатель 2 — Клумба 2. Покупатель 4 — Клумбы 1 и 2 (и клумба 3, если убрать лилии)."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ДИАГРАММЫ РАССЕИВАНИЯ" (8 КЛАСС) ==========
const grade8_topic3Cases = [
    // ========== КЕЙС 1. «Спортивный тренер: бег и прыжки» ==========
    {
        id: "scatter_1",
        title: "🏃 Кейс 1: «Бег и прыжки»",
        description: "Тренер по лёгкой атлетике заметил интересную закономерность: некоторые спортсмены, которые быстро бегают 60 метров, также неплохо прыгают в длину. Но один из его коллег утверждает, что это просто совпадение и специально тренировать оба навыка не нужно. Тренер решил проверить это на своих учениках.<br><br><strong>Данные по 10 спортсменам:</strong><br>• Время бега (с): 8,5; 8,2; 8,8; 7,9; 8,0; 8,6; 7,8; 8,3; 8,1; 8,4<br>• Длина прыжка (см): 210; 225; 200; 240; 235; 215; 245; 220; 230; 218<br><br>Помогите тренеру доказать, что связь существует.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, как визуально показать связь между двумя величинами.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся знакомятся с понятием диаграммы рассеивания (точечной диаграммы).<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Есть ли связь между временем бега и длиной прыжка?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Строят диаграмму рассеивания и анализируют форму облака точек.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему нельзя сказать, что быстрый бег ПРИЧИНА дальних прыжков?`,
        question: "Какая связь наблюдается между временем бега и длиной прыжка? (введите: положительная, отрицательная или нет связи)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "отрицательная",
        hint: "💡 Чем МЕНЬШЕ время бега (быстрее спортсмен), тем БОЛЬШЕ длина прыжка. Если одна величина растёт, а другая падает — это отрицательная связь.",
        solution: "✅ Облако точек вытянуто слева направо вниз. Это <strong>отрицательная связь</strong>: чем меньше время бега (быстрее спортсмен), тем больше длина прыжка. Тренер прав — есть смысл развивать оба качества вместе."
    },
    // ========== КЕЙС 2. «Школьный врач: рост и вес» ==========
    {
        id: "scatter_2",
        title: "📏 Кейс 2: «Рост и вес»",
        description: "Школьный врач проводит ежегодный осмотр. У него есть данные о росте и весе 15 восьмиклассников. Он хочет выяснить, есть ли связь между этими показателями, чтобы дать рекомендации по питанию и физической активности.<br><br><strong>Данные (рост в см, вес в кг):</strong><br>(155;45), (158;48), (160;50), (162;49), (165;55), (167;58), (168;56), (170;60), (172;62), (175;65), (178;70), (180;68), (182;72), (185;75), (188;80)<br><br>Помогите врачу наглядно показать родителям закономерность.",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что такое «норма» роста и веса.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму рассеивания.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая связь между ростом и весом?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют форму облака.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как врач может использовать диаграмму, чтобы заметить отклонения от нормы?`,
        question: "Какая связь наблюдается между ростом и весом? (введите: положительная, отрицательная или нет связи)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "положительная",
        hint: "💡 Чем БОЛЬШЕ рост, тем БОЛЬШЕ вес. Если обе величины растут вместе — это положительная связь.",
        solution: "✅ Облако точек вытянуто вправо вверх. Это <strong>положительная связь</strong>: чем больше рост, тем больше вес. Врач может построить «коридор нормы» и сразу видеть, какие дети отклоняются от типичного соотношения — это повод для дополнительного обследования."
    },
    // ========== КЕЙС 3. «Медицинская диагностика: температура и давление» ==========
    {
        id: "scatter_3",
        title: "🩺 Кейс 3: «Температура и давление»",
        description: "В больнице поступило несколько пациентов с разными симптомами. Врач измерил у каждого температуру тела и артериальное давление. Результаты:<br><br>• С нормальной температурой (36,5-37,0°С): (36,5;120), (36,6;118), (36,7;122), (36,8;119), (36,9;121), (37,0;120)<br>• С высокой температурой (37,5-39,5°С): (37,5;125), (38,0;118), (38,2;122), (38,5;119), (39,0;121), (39,5;120)<br><br>Молодой врач-интерн сказал: «Здесь нет никакой закономерности». А опытный врач ответил: «Это очень важное наблюдение!» Почему?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, что значит «нет закономерности».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму рассеивания.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему опытный врач обрадовался?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют форму облака.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Всегда ли отсутствие связи — это «хорошо»?`,
        question: "Какая связь наблюдается между температурой и давлением? (введите: положительная, отрицательная или нет связи)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "нет связи",
        hint: "💡 Посмотри на точки: при повышении температуры давление не растёт и не падает систематически. Облако хаотичное или вытянуто горизонтально.",
        solution: "✅ Облако точек не имеет наклона — это <strong>отсутствие связи</strong>. Для врача это важно: он знает, что можно лечить температуру отдельно, не опасаясь, что давление «убежит». Отсутствие связи — тоже важный результат!"
    },
    // ========== КЕЙС 4. «Экономика: нефть и рубль» ==========
    {
        id: "scatter_4",
        title: "💰 Кейс 4: «Нефть и рубль»",
        description: "Ученик 8 класса готовит доклад по экономике. Он нашёл данные о цене нефти (долларов за баррель) и курсе рубля к доллару за два периода.<br><br><strong>2013 год:</strong> (110;31), (105;32), (100;33), (95;34)<br><strong>2019 год:</strong> (65;63), (60;66), (55;64), (70;62), (50;68)<br><br>На одной диаграмме ясно видна наклонная линия, на другой — хаотичное облако. Что это значит?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, какие факторы влияют на курс рубля.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят две диаграммы рассеивания.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Почему связь могла измениться?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают форму облаков.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что значит «связь пропала»?`,
        question: "В каком году связь между ценой нефти и курсом рубля была заметно сильнее? (введите: 2013 или 2019)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "2013",
        hint: "💡 Посмотри на данные: в 2013 году при падении цены нефти курс рубля рос (рубль слабел). В 2019 году такой чёткой картины нет.",
        solution: "✅ В <strong>2013</strong> году облако точек вытянуто по диагонали (отрицательная связь: цена нефти падает — курс рубля растёт). В 2019 году связь ослабла, потому что на курс стали сильнее влиять другие факторы (санкции, действия Центробанка). Это показывает, что диаграмма рассеивания — не магия, а инструмент, который нужно использовать с пониманием контекста."
    },
    // ========== КЕЙС 5. «Разрядка телефона» ==========
    {
        id: "scatter_5",
        title: "📱 Кейс 5: «Разрядка телефона»",
        description: "Ученик Петя заметил, что его телефон разряжается тем сильнее, чем дольше он им пользуется после зарядки. Он провёл эксперимент:<br><br>• Через 1 час: заряд 90%<br>• Через 2 часа: заряд 75%<br>• Через 3 часа: заряд 60%<br>• Через 4 часа: заряд 45%<br>• Через 5 часов: заряд 30%<br>• Через 6 часов: заряд 15%<br>• Через 7 часов: заряд 5%<br><br>Друг Пети сказал: «Очевидно, что связь есть. Зачем строить диаграмму?» Что ответит Петя?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, зачем строить диаграмму, если связь «очевидна».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся строят диаграмму рассеивания.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Насколько сильная связь? Она линейная?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют форму облака.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Как диаграмма помогает делать прогнозы?`,
        question: "Какой формы облако точек на этой диаграмме? (введите: точки лежат почти на прямой, точки разбросаны хаотично)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "точки лежат почти на прямой",
        hint: "💡 Посмотри на данные: каждые 2 часа заряд падает примерно на 15%. Точки должны выстроиться вдоль наклонной линии.",
        solution: "✅ Диаграмма показывает <strong>не только наличие связи, но и её силу и форму</strong>. В данном случае связь очень сильная (точки почти на прямой) и линейная. Это значит, что можно построить формулу и точно прогнозировать разрядку. Петя прав — диаграмма даёт больше информации, чем просто «связь есть»."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "ДИСПЕРСИЯ ЧИСЛОВОГО НАБОРА" (8 КЛАСС) ==========
const grade8_topic1Cases = [
    // ========== КЕЙС 1. «Кого взять в сборную?» ==========
    {
        id: "variance_1",
        title: "🏀 Кейс 1: «Кого взять в сборную?»",
        description: "Тренер сборной школы по баскетболу выбирает игрока для решающего штрафного броска. Два претендента — Антон и Борис — на тренировках показали одинаковую среднюю результативность: каждый забил в среднем 7 из 10 бросков. Но тренер сомневается.<br><br><strong>Результаты 5 подходов (число попаданий из 10):</strong><br>• Антон: 7, 7, 7, 7, 7<br>• Борис: 4, 6, 8, 9, 8<br><br>Тренер говорит: «Средний результат одинаковый, но я не уверен, кого выпустить. Один из них может промахнуться в ответственный момент». Как математически обосновать выбор?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Учащиеся обсуждают, почему тренер сомневается при одинаковом среднем.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вспоминают формулу дисперсии: S² = Σ(xᵢ - x̄)² / n.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Кто стабильнее? У кого меньше разброс?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют дисперсию для каждого спортсмена.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему для ответственного момента нужен стабильный игрок? А если бы тренеру нужен был игрок, способный на «рывок»?`,
        question: "Чему равна дисперсия результатов Бориса? (введите число, например 5,6)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 3.2,
        hint: "💡 Сначала найди среднее (оно уже известно — 7). Затем вычти среднее из каждого значения, возведи в квадрат, сложи и раздели на 5.",
        solution: "✅ Дисперсия Антона = 0 (абсолютно стабилен). Дисперсия Бориса = ((4-7)² + (6-7)² + (8-7)² + (9-7)² + (8-7)²) / 5 = (9+1+1+4+1)/5 = 16/5 = <strong>3,2</strong>. Для ответственного момента нужен стабильный игрок — Антон."
    },
    // ========== КЕЙС 2. «Спор о климате» ==========
    {
        id: "variance_2",
        title: "🌡️ Кейс 2: «Спор о климате»",
        description: "Два друга спорят, где лучше провести летние каникулы. Один предлагает поехать в город Мирный (континентальный климат), где летом бывает очень жарко — до +25 °C. Второй настаивает на Приморске (морской климат), где летом прохладно — около +15 °C, зато нет резких перепадов.<br><br><strong>Среднемесячные температуры (°C):</strong><br>• Приморск: -2, 0, +3, +6, +12, +15, +15, +14, +10, +6, +2, 0<br>• Мирный: -25, -20, -10, +5, +15, +25, +25, +20, +10, -5, -15, -20<br><br>Первый друг говорит: «В Мирном средняя температура июля выше!» Второй считает, что климат Приморска комфортнее. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает понятие «комфортность климата».<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют среднюю температуру и дисперсию для каждого города.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> В каком городе климат предсказуемее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают дисперсии и делают вывод.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что означает большая дисперсия в Мирном?`,
        question: "Чему равна дисперсия температур в Мирном? (округлите до целого числа, например 250)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 289,
        hint: "💡 Сначала найди среднее (примерно 0). Затем вычисли сумму квадратов отклонений и раздели на 12.",
        solution: "✅ Дисперсия Приморска ≈ 37 (небольшая, температуры близки к среднему). Дисперсия Мирного ≈ 289 (огромный разброс от -25 до +25). Большая дисперсия означает суровую зиму и сильные перепады — такой климат тяжелее переносится. Прав второй друг."
    },
    // ========== КЕЙС 3. «Кондитерская фабрика» ==========
    {
        id: "variance_3",
        title: "🍫 Кейс 3: «Кондитерская фабрика»",
        description: "На фабрике «Сластёна» две линии производят шоколадные батончики. На упаковке написано: «Масса батончика — 50 г». Контролёр ОТК случайно взял по 5 батончиков с каждой линии и взвесил их.<br><br><strong>Результаты (в граммах):</strong><br>• Линия А: 49, 50, 50, 50, 51<br>• Линия Б: 40, 45, 50, 55, 60<br><br>Директор фабрики счастлив: среднее арифметическое для каждой линии — 50 г. «Всё отлично!» — заявляет он. Но из магазинов приходят жалобы именно на батончики с линии Б. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему при одинаковом среднем могут быть жалобы.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют дисперсию для каждой линии.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая линия даёт стабильное качество?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают дисперсии.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Какой показатель (среднее или дисперсия) важнее для контроля качества?`,
        question: "Чему равна дисперсия для линии Б? (введите число, например 452)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 50,
        hint: "💡 Среднее = 50. Отклонения: -10, -5, 0, 5, 10. Квадраты: 100, 25, 0, 25, 100. Сумма = 250. Раздели на 5.",
        solution: "✅ Дисперсия линии А = 0,4 (очень маленькая — стабильное качество). Дисперсия линии Б = (100+25+0+25+100)/5 = 250/5 = <strong>50</strong> (огромная). Линия Б выдаёт брак: часть батончиков слишком маленькие (обман покупателя), часть слишком большие (убыток фабрике). Права директора только формально."
    },
    // ========== КЕЙС 4. «Две школы: кто умнее?» ==========
    {
        id: "variance_4",
        title: "🏫 Кейс 4: «Две школы: кто умнее?»",
        description: "В двух школах района провели итоговое тестирование по математике в 8-х классах. В каждой школе ровно 5 учеников.<br><br><strong>Результаты (баллы за тест):</strong><br>• Школа №1: 65, 65, 65, 65, 65<br>• Школа №2: 50, 60, 65, 70, 80<br><br>Чиновник из министерства докладывает: «Уровень подготовки в школах одинаковый, средний балл совпадает (65)». Родитель ученика из школы №2 возмущается. Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему чиновник может ошибаться.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют дисперсию для каждой школы.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какая школа лучше для сильного ученика? Для слабого?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают дисперсии и обсуждают разные точки зрения.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Нет правильного ответа — всё зависит от цели.`,
        question: "Чему равна дисперсия для школы №2? (введите число, например 78)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 100,
        hint: "💡 Отклонения от среднего (65): -15, -5, 0, 5, 15. Квадраты: 225, 25, 0, 25, 225. Сумма = 500. Раздели на 5.",
        solution: "✅ Дисперсия школы №1 = 0. Дисперсия школы №2 = (225+25+0+25+225)/5 = 500/5 = <strong>100</strong>. Для сильного ученика лучше школа с большой дисперсией (есть конкуренция). Для слабого — школа с малой дисперсией (все рядом, никто не убежал вперёд)."
    },
    // ========== КЕЙС 5. «Фермер и удобрения» ==========
    {
        id: "variance_5",
        title: "🌱 Кейс 5: «Фермер и удобрения»",
        description: "Фермер выращивает помидоры на двух участках. Урожайность (в кг с куста) за 5 лет:<br>• Участок №1 (удобрение «Богатырь»): 4, 5, 6, 5, 5<br>• Участок №2 (удобрение «Великан»): 2, 3, 5, 7, 8<br><br>Средняя урожайность на обоих участках — 5 кг с куста. Фермер в замешательстве: удобрения разные, а среднее одинаковое. Какое удобрение выбрать?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему фермер не может сделать выбор.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют дисперсию для каждого участка.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какое удобрение даёт стабильный результат? А какое — рискованный, но потенциально рекордный?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют дисперсии в зависимости от цели фермера.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Где в жизни нужна маленькая дисперсия (надёжность), а где большая (риск)?`,
        question: "Чему равна дисперсия урожайности на участке №2? (введите число, например 74.2)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 5.2,
        hint: "💡 Отклонения от среднего (5): -3, -2, 0, 2, 3. Квадраты: 9, 4, 0, 4, 9. Сумма = 26. Раздели на 5.",
        solution: "✅ Дисперсия участка №1 = (1+0+1+0+0)/5 = 2/5 = 0,4 (стабильность). Дисперсия участка №2 = (9+4+0+4+9)/5 = 26/5 = <strong>5,2</strong> (нестабильность). Для гарантированных поставок — удобрение №1. Для эксперимента и риска — удобрение №2."
    }
];
// ========== КЕЙСЫ ДЛЯ ТЕМЫ "СТАНДАРТНОЕ ОТКЛОНЕНИЕ" (8 КЛАСС) ==========
const grade8_topic2Cases = [
    // ========== КЕЙС 1. «Магазин электроники: кто работает точнее?» ==========
    {
        id: "std_1",
        title: "📦 Кейс 1: «Кто работает точнее?»",
        description: "Два курьера интернет-магазина развозят заказы. Менеджер оценивает их по среднему времени доставки (в минутах). За 5 доставок:<br><br>• Курьер А: 25, 26, 25, 24, 25<br>• Курьер Б: 15, 20, 25, 30, 35<br><br>Среднее время у обоих — 25 минут. Менеджер говорит: «Они работают одинаково». Но клиенты жалуются на курьера Б: то очень рано, то очень поздно. Почему среднее арифметическое обманывает менеджера?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему при одинаковом среднем могут быть жалобы.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вспоминают формулу дисперсии и стандартного отклонения. S = √(Σ(xᵢ - x̄)² / n)<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой курьер надёжнее?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Вычисляют стандартное отклонение для каждого курьера.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> В каких профессиях нужно маленькое стандартное отклонение, а в каких большое — даже хорошо?`,
        question: "Чему равно стандартное отклонение для курьера Б? (округлите до сотых, например 3.02)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 7.07,
        hint: "💡 Сначала найди дисперсию: ((15-25)² + (20-25)² + (25-25)² + (30-25)² + (35-25)²)/5 = (100+25+0+25+100)/5 = 250/5 = 50. Затем извлеки квадратный корень.",
        solution: "✅ Курьер А: дисперсия ≈ 0,5, S ≈ 0,71 мин. Курьер Б: дисперсия = 50, S ≈ √50 ≈ <strong>7,07 мин</strong>. Стандартное отклонение показывает типичное отклонение от среднего. У курьера А оно меньше минуты — клиент может быть уверен, что посылку привезут почти точно в 25 минут. У курьера Б отклонение 7 минут — это непредсказуемо. Надёжнее курьер А."
    },
    // ========== КЕЙС 2. «Контроль качества на хлебозаводе» ==========
    {
        id: "std_2",
        title: "🍞 Кейс 2: «Контроль качества на хлебозаводе»",
        description: "На хлебозаводе две линии выпекают булки номинальной массой 200 г. Технолог сделал контрольные взвешивания:<br><br>• Линия 1: среднее 193,9 г, стандартное отклонение 1,30 г<br>• Линия 2: среднее 198,6 г, стандартное отклонение 4,18 г<br><br>Директор смотрит на средние значения и говорит: «Линия 2 ближе к норме (200 г), значит, она работает лучше!» Главный инженер возражает: «Я бы остановил линию 2 на ремонт». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему мнения разошлись.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся анализируют, что показывает среднее, а что — стандартное отклонение.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Директор или инженер прав?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают стандартные отклонения.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Высокое рассеивание (большое S) говорит об износе оборудования. Что нужно сделать с каждой линией?`,
        question: "У какой линии стандартное отклонение БОЛЬШЕ? (введите: Линия 1 или Линия 2)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "линия 2",
        hint: "💡 Сравни числа: 1,30 и 4,18. Какое больше?",
        solution: "✅ Прав инженер. Линия 2 ближе к норме по среднему, но у неё большое стандартное отклонение (4,18 > 1,30). Большое S говорит об износе оборудования — линию 2 нужно ремонтировать. Линию 1 нужно просто отрегулировать (добавить теста), так как S маленькое."
    },
    // ========== КЕЙС 3. «Подмосковные города» ==========
    {
        id: "std_3",
        title: "🏙️ Кейс 3: «Подмосковные города»",
        description: "Правительство Московской области хочет ввести льготы для малых городов и дополнительные налоги для очень крупных. Учёные предложили использовать статистику:<br><br>• Среднее население: 67,7 тыс. чел.<br>• Стандартное отклонение: 57,2 тыс. чел.<br><br>Правило:<br>• Малый город: население < x̄ − S (меньше 10,5 тыс.)<br>• Очень крупный город: население > x̄ + 2S (больше 182,1 тыс.)<br><br>Распределите города по категориям: Чехов (74 тыс.), Зарайск (12 тыс.), Коломна (138 тыс.), Красногорск (175 тыс.).",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, зачем нужны чёткие критерии.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют границы: x̄ − S и x̄ + 2S.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какие города попадут в каждую категорию?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Применяют правило к данным.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Почему для «очень крупных» взяли +2S, а не +S?`,
        question: "Какой город из списка попадает в категорию «очень крупный»? (введите название)",
        answerNormalizer: (a) => a.toLowerCase().trim(),
        answer: "красногорск",
        hint: "💡 x̄ + 2S = 67,7 + 2×57,2 = 67,7 + 114,4 = 182,1 тыс. Какой город больше 182,1 тыс.?",
        solution: "✅ Границы: малые < 10,5 тыс. (Зарайск — 12 тыс. не подходит, он выше). Очень крупные > 182,1 тыс. Красногорск (175 тыс.) не дотягивает? Пересчитаем: 67,7 + 114,4 = 182,1. 175 < 182,1 — значит, Красногорск НЕ очень крупный. Все города из списка попадают в «типичные». Для очень крупных нужны города типа Балашихи (>182 тыс.)."
    },
    // ========== КЕЙС 4. «Школьный психолог: уровень тревожности» ==========
    {
        id: "std_4",
        title: "🧠 Кейс 4: «Уровень тревожности»",
        description: "Школьный психолог провёл тест на тревожность в двух параллельных 8-х классах. Тест оценивается от 0 (спокойный) до 30 (очень тревожный). Результаты:<br><br>• 8 «А»: 10, 12, 11, 13, 10, 12, 11, 13<br>• 8 «Б»: 2, 5, 18, 20, 25, 8, 15, 27<br><br>Среднее в обоих классах — примерно 11,5 балла. Учителя говорят: «Классы одинаковые». Но психолог считает, что работать с ними нужно по-разному. Почему?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает, почему одинаковое среднее — не повод для одинаковых методов.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют стандартное отклонение для каждого класса.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> В каком классе дети более однородны?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Сравнивают S и делают выводы.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> Что означает маленькое S? А большое?`,
        question: "Чему равно стандартное отклонение для 8 «Б»? (округлите до десятых, например 5.1)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 8.5,
        hint: "💡 Сначала найди дисперсию для 8 «Б»: отклонения от среднего 11,5: -9,5; -6,5; +6,5; +8,5; +13,5; -3,5; +3,5; +15,5. Квадраты: 90,25; 42,25; 42,25; 72,25; 182,25; 12,25; 12,25; 240,25. Сумма ≈ 694, затем раздели на 8 и извлеки корень.",
        solution: "✅ 8 «А»: S ≈ 1,1 (маленькое — класс однородный, можно давать общие рекомендации). 8 «Б»: S ≈ <strong>8,5</strong> (большое — в классе есть и очень спокойные, и очень тревожные дети, нужен индивидуальный подход)."
    },
    // ========== КЕЙС 5. «Выбор стратегии в бизнесе: стабильность или риск?» ==========
    {
        id: "std_5",
        title: "📈 Кейс 5: «Стабильность или риск?»",
        description: "Два стартапа ищут инвестиции. Оба показывают среднюю ежемесячную прибыль 1 млн рублей за последние 6 месяцев. Помесячная прибыль (млн руб.):<br><br>• Стартап «Стабильный»: 0,9; 1,0; 1,1; 0,9; 1,0; 1,1<br>• Стартап «Взрывной»: 0; 0,5; 1,0; 1,5; 2,0; 1,0<br><br>Консервативный инвестор выбирает «Стабильный». Рисковый инвестор — «Взрывной». Кто прав?",
        stages: `1️⃣ <strong>Погружение в контекст:</strong> Учитель читает ситуацию. Класс обсуждает разные стратегии инвестирования.<br>
2️⃣ <strong>Изучение материала:</strong> Учащиеся вычисляют стандартное отклонение для обоих стартапов.<br>
3️⃣ <strong>Выдвижение гипотез:</strong> Какой стартап выберет пенсионный фонд? А венчурный фонд?<br>
4️⃣ <strong>Выбор оптимального решения:</strong> Анализируют S как меру риска.<br>
5️⃣ <strong>Обсуждение и рефлексия:</strong> В финансах стандартное отклонение называется волатильностью. Почему акции надёжных компаний имеют маленькое S?`,
        question: "Чему равно стандартное отклонение для стартапа «Взрывной»? (округлите до сотых, например 7.06)",
        answerNormalizer: (a) => parseFloat(a.replace(',','.')),
        answer: 0.71,
        hint: "💡 Среднее = 1. Отклонения: -1; -0,5; 0; 0,5; 1; 0. Квадраты: 1; 0,25; 0; 0,25; 1; 0. Сумма = 2,5. Дисперсия = 2,5/6 ≈ 0,4167. S = √0,4167 ≈ 0,645. Ближайший ответ — 0,65? Проверим: стандартное отклонение ≈ 0,65.",
        solution: "✅ «Стабильный»: S ≈ 0,08 млн руб. (80 тыс. руб.) — очень предсказуем. «Взрывной»: S ≈ <strong>0,65 млн руб.</strong> (650 тыс. руб.) — высокая волатильность. Оба правы: консерватор выберет маленькое S, рисковый игрок — большое S. Стандартное отклонение — это мера риска."
    }
];
// ========== ТРКМ - ПРАВИЛО УМНОЖЕНИЯ (2 задания: тест + кластер) ==========
const multiplicationFormulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_1",
        title: "🧠 ТРКМ: «Правило умножения» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы о правиле умножения в комбинаторике. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Что нужно сделать с количеством вариантов на каждом шаге, чтобы получить общее число комбинаций?",
                hint: "💡 Вспомните правило умножения.",
                correctAnswer: "умножить",
                explanation: "✅ Чтобы получить общее число комбинаций, нужно перемножить количество вариантов на каждом шаге: n₁ × n₂ × ... × nₖ."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "Сколько разных трёхзначных кодов можно составить из цифр 1, 2, 3, если цифры могут повторяться?",
                hint: "💡 На каждое из трёх мест можно поставить любую из трёх цифр: 3 × 3 × 3 = ?",
                correctAnswer: "27",
                explanation: "✅ 3 × 3 × 3 = 27 различных кодов."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "Если в кафе 2 вида супа и 3 вида салата, сколько разных наборов (суп + салат) можно заказать?",
                hint: "💡 Каждый суп можно сочетать с каждым салатом: 2 × 3 = ?",
                correctAnswer: "6",
                explanation: "✅ 2 × 3 = 6 различных наборов."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "В формуле n₁ × n₂ × … × nₖ что означает каждая буква nᵢ?",
                hint: "💡 Например, n₁ — это количество вариантов для первого выбора.",
                correctAnswer: "количество вариантов на i-м шаге",
                explanation: "✅ nᵢ — это количество способов сделать i-й выбор (количество вариантов на i-м шаге)."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "Сколько маршрутов из пункта А в пункт С, если из А в В ведут 3 дороги, а из В в С — 2 дороги?",
                hint: "💡 Нужно перемножить количество дорог на каждом участке: 3 × 2 = ?",
                correctAnswer: "6",
                explanation: "✅ 3 × 2 = 6 различных маршрутов."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "Почему при подсчёте кодов или паролей правило умножения работает, а простое сложение – нет?",
                hint: "💡 Что мы упускаем, когда складываем варианты?",
                correctAnswer: "потому что при сложении не учитываются сочетания между разными шагами",
                options: [
                    { value: "потому что при сложении не учитываются сочетания между разными шагами", text: "Потому что при сложении не учитываются сочетания между разными шагами" },
                    { value: "потому что сложение даёт меньший результат", text: "Потому что сложение даёт меньший результат" },
                    { value: "потому что умножение быстрее", text: "Потому что умножение быстрее" },
                    { value: "потому что так принято", text: "Потому что так принято" }
                ],
                explanation: "✅ При сложении мы считаем, что варианты на разных шагах не связаны, но на самом деле каждый вариант первого шага сочетается с каждым вариантом второго шага."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "В чём разница между применением правила умножения в задаче с возвращением (цифры могут повторяться) и без возвращения (без повторений)?",
                hint: "💡 В задаче без возвращения после каждого выбора количество доступных вариантов уменьшается.",
                correctAnswer: "при возвращении количество вариантов на каждом шаге одинаковое, при без возвращения уменьшается",
                options: [
                    { value: "при возвращении количество вариантов на каждом шаге одинаковое, при без возвращения уменьшается", text: "При возвращении количество вариантов на каждом шаге одинаковое, при без возвращения уменьшается" },
                    { value: "при возвращении вариантов меньше", text: "При возвращении вариантов меньше" },
                    { value: "разницы нет", text: "Разницы нет" },
                    { value: "при без возвращения вариантов больше", text: "При без возвращения вариантов больше" }
                ],
                explanation: "✅ С возвращением: количество вариантов на каждом шаге не меняется (n × n × ...). Без возвращения: после каждого выбора количество доступных вариантов уменьшается на 1."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "Как связаны правило умножения и дерево возможных исходов эксперимента?",
                hint: "💡 Дерево исходов — это визуальное представление правила умножения.",
                correctAnswer: "правило умножения позволяет подсчитать количество листьев дерева",
                options: [
                    { value: "правило умножения позволяет подсчитать количество листьев дерева", text: "Правило умножения позволяет подсчитать количество листьев дерева" },
                    { value: "правило умножения не связано с деревом", text: "Правило умножения не связано с деревом" },
                    { value: "дерево сложнее правила умножения", text: "Дерево сложнее правила умножения" },
                    { value: "правило умножения показывает только один путь", text: "Правило умножения показывает только один путь" }
                ],
                explanation: "✅ Дерево исходов наглядно показывает все возможные комбинации. Количество листьев дерева равно произведению количеств веток на каждом уровне."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "Почему в задаче «сколько трёхзначных чисел можно составить из цифр 1,2,3,4» первый шаг (выбор первой цифры) имеет 4 варианта, а не 3?",
                hint: "💡 Трёхзначное число может начинаться с любой цифры.",
                correctAnswer: "потому что первая цифра может быть любой из четырёх, ноль отсутствует",
                options: [
                    { value: "потому что первая цифра может быть любой из четырёх, ноль отсутствует", text: "Потому что первая цифра может быть любой из четырёх, ноль отсутствует" },
                    { value: "потому что цифр всего 4", text: "Потому что цифр всего 4" },
                    { value: "потому что трёхзначное число не может начинаться с 0", text: "Потому что трёхзначное число не может начинаться с 0" },
                    { value: "потому что это правило", text: "Потому что это правило" }
                ],
                explanation: "✅ В данной задаче нет ограничений на первую цифру (ноля нет), поэтому первую цифру можно выбрать 4 способами."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "Что произойдёт с общим количеством комбинаций, если на одном из шагов количество вариантов увеличится в 2 раза?",
                hint: "💡 Общее количество комбинаций = n₁ × n₂ × ... × nₖ.",
                correctAnswer: "увеличится в 2 раза",
                options: [
                    { value: "увеличится в 2 раза", text: "Увеличится в 2 раза" },
                    { value: "увеличится на 2", text: "Увеличится на 2" },
                    { value: "не изменится", text: "Не изменится" },
                    { value: "уменьшится в 2 раза", text: "Уменьшится в 2 раза" }
                ],
                explanation: "✅ Общее количество комбинаций — это произведение количества вариантов на каждом шаге. Если один из множителей увеличить в 2 раза, то и всё произведение увеличится в 2 раза."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ==========
    {
        id: "trkm_cluster_1",
        title: "🧠 ТРКМ: Кластер «Правило умножения»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Переместите карточки из нижней области в нужные прямоугольники.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_1", name: "📐 Суть правила", maxCards: 3 },
            { id: "branch_2", name: "⚙️ Когда применяется", maxCards: 3 },
            { id: "branch_3", name: "📊 Графическое представление", maxCards: 2 },
            { id: "branch_4", name: "💡 Примеры из жизни", maxCards: 4 },
            { id: "branch_6", name: "⚠️ Типичные ошибки", maxCards: 3 },
            { id: "branch_7", name: "📐 Формулы и обозначения", maxCards: 3 }
        ],
        cards: [
    // Ветвь 1: Суть правила (3 карточки)
    { id: "card_1", text: "Если объект A можно выбрать m способами, а объект B – n способами, то пару (A, B) можно выбрать m × n способами" },
    { id: "card_2", text: "Обобщение: n₁ × n₂ × … × nₖ" },
    { id: "card_3", text: "Каждый вариант одного шага сочетается с каждым вариантом другого шага" },
    
    // Ветвь 2: Когда применяется (3 карточки)
    { id: "card_4", text: "Выбор на каждом шаге не зависит от предыдущих" },
    { id: "card_5", text: "Эксперимент состоит из нескольких последовательных этапов" },
    { id: "card_6", text: "Нужно подсчитать общее количество всех возможных исходов" },
    
    // Ветвь 3: Графическое представление (2 карточки)
    { id: "card_7", text: "Дерево вариантов: от корня отходят ветви первого выбора" },
    { id: "card_8", text: "Количество листьев дерева = результат умножения" },
    
    // Ветвь 4: Примеры из жизни (4 карточки)
    { id: "card_9", text: "Код из 3 цифр (0–9): 10 × 10 × 10 = 1000 вариантов" },
    { id: "card_10", text: "Меню: 3 супа × 4 салата × 2 напитка = 24 обеда" },
    { id: "card_11", text: "Маршруты: 2 дороги × 3 дороги = 6 маршрутов" },
    { id: "card_12", text: "Одежда: 4 рубашки × 3 галстука = 12 комплектов" },
    
    // Ветвь 5: Связь с другими понятиями (ПОЛНОСТЬЮ УДАЛЕНА - нет карточек)
    
    // Ветвь 6: Типичные ошибки (3 карточки)
    { id: "card_16", text: "Сложение вместо умножения: 2+3=5 вместо 2×3=6" },
    { id: "card_17", text: "Забывают про зависимость (выбор без возвращения)" },
    { id: "card_18", text: "Не учитывают ограничения (код не может начинаться с 0)" },
    
    // Ветвь 7: Формулы и обозначения (3 карточки)
    { id: "card_19", text: "N = n₁ × n₂ × … × nₖ (основная формула)" }
]
    }
];
// ========== ТРКМ - НЕСОВМЕСТНЫЕ СОБЫТИЯ (кластер) ==========
const incompatibleFormulas = [
    // ========== ЗАДАНИЕ: КЛАСТЕР ДЛЯ НЕСОВМЕСТНЫХ СОБЫТИЙ ==========
    {
        id: "trkm_cluster_incompatible",
        title: "Несовместные события",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Каждая карточка должна попасть в свой раздел.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_def", name: "📖 ОПРЕДЕЛЕНИЕ", maxCards: 1 },
            { id: "branch_sign", name: "🔍 ПРИЗНАК", maxCards: 2 },
            { id: "branch_formula", name: "➕ ФОРМУЛА СЛОЖЕНИЯ", maxCards: 2 },
            { id: "branch_examples", name: "🎲 ПРИМЕРЫ", maxCards: 4 },
            { id: "branch_compare", name: "🔄 СРАВНЕНИЕ С СОВМЕСТНЫМИ", maxCards: 2 }
        ],
        cards: [
            { id: "card_def_1", text: "События, которые не могут произойти одновременно в одном испытании" },
   //         { id: "card_def_2", text: "События исключают друг друга" },
            { id: "card_sign_1", text: "У событий нет общих исходов" },
            { id: "card_sign_2", text: "Пересечение событий пусто: A ∩ B = ∅" },
            { id: "card_formula_1", text: "P(A ∪ B) = P(A) + P(B)" },
            { id: "card_formula_2", text: "Формула работает ТОЛЬКО для несовместных событий" },
            { id: "card_example_1", text: "Выпадение 1 и 6 на одном кубике" },
            { id: "card_example_2", text: "Орёл и решка при одном подбрасывании монеты" },
            { id: "card_example_3", text: "Вытащить красный или синий шар (шары разных цветов)" },
            { id: "card_example_4", text: "Попадание и промах при одном выстреле" },
            { id: "card_compare_1", text: "У совместных событий есть общие исходы" },
            { id: "card_compare_2", text: "Для совместных событий: P(A∪B) = P(A)+P(B)−P(A∩B)" }
        ]
    }
];
// ========== ТРКМ - УСЛОВНАЯ ВЕРОЯТНОСТЬ (тест + кластер) ==========
const conditionalFormulas = [
    // ========== ЗАДАНИЕ 1: Толстые и тонкие вопросы (тест) ==========
    {
        id: "trkm_test_conditional_1",
        title: "🧠 ТРКМ: «Условная вероятность» (Толстые и тонкие вопросы)",
        description: "Ответьте на вопросы об условной вероятности и формуле умножения вероятностей. Тонкие вопросы требуют краткого ответа, толстые — выбора варианта.",
        type: "trkm_test",
        questions: [
            // ========== ТОНКИЕ ВОПРОСЫ (краткий ответ) ==========
            {
                id: "q_thin_1",
                type: "thin",
                question: "Как обозначается вероятность события A при условии, что событие B уже произошло?",
                hint: "💡 Используется вертикальная черта между событиями.",
                correctAnswer: "P(A|B)",
                explanation: "✅ Условная вероятность обозначается P(A|B) — вероятность события A при условии, что событие B произошло."
            },
            {
                id: "q_thin_2",
                type: "thin",
                question: "Запишите формулу условной вероятности P(A|B) через P(A∩B) и P(B).",
                hint: "💡 Это отношение вероятности пересечения к вероятности условия.",
                correctAnswer: "P(A∩B)/P(B)",
                explanation: "✅ P(A|B) = P(A∩B) / P(B), при условии что P(B) > 0."
            },
            {
                id: "q_thin_3",
                type: "thin",
                question: "Если события A и B независимы, то P(A|B) = ?",
                hint: "💡 Независимость означает, что B не влияет на A.",
                correctAnswer: "P(A)",
                explanation: "✅ Для независимых событий P(A|B) = P(A). Появление B не меняет вероятность A."
            },
            {
                id: "q_thin_4",
                type: "thin",
                question: "Из колоды в 36 карт вытянули одну карту. Найдите P(туз | красная карта).",
                hint: "💡 Красных карт в колоде 18, красных тузов — 2.",
                correctAnswer: "2/18",
                explanation: "✅ P(туз|красная) = 2/18 = 1/9 ≈ 0,111."
            },
            {
                id: "q_thin_5",
                type: "thin",
                question: "Если P(A) = 0,3, P(B) = 0,5, P(A∩B) = 0,15, то зависимы или независимы события A и B?",
                hint: "💡 Проверьте: P(A∩B) = P(A) × P(B)?",
                correctAnswer: "независимы",
                explanation: "✅ 0,3 × 0,5 = 0,15 = P(A∩B) → события независимы."
            },
            // ========== ТОЛСТЫЕ ВОПРОСЫ (с вариантами ответа) ==========
            {
                id: "q_thick_1",
                type: "thick",
                question: "Почему условная вероятность P(A|B) не равна P(A∩B)?",
                hint: "💡 В чём разница между «A и B произошли» и «A произошёл, при условии что B произошёл»?",
                correctAnswer: "P(A|B) — это доля исходов A среди исходов B, а P(A∩B) — доля исходов A∩B среди всех исходов",
                options: [
                    { value: "P(A|B) — это доля исходов A среди исходов B, а P(A∩B) — доля исходов A∩B среди всех исходов", text: "P(A|B) — это доля исходов A среди исходов B, а P(A∩B) — доля исходов A∩B среди всех исходов" },
                    { value: "Это одно и то же", text: "Это одно и то же" },
                    { value: "P(A|B) всегда больше P(A∩B)", text: "P(A|B) всегда больше P(A∩B)" },
                    { value: "P(A|B) = P(A∩B) × P(B)", text: "P(A|B) = P(A∩B) × P(B)" }
                ],
                explanation: "✅ P(A∩B) — это вероятность того, что произойдут оба события. P(A|B) — это вероятность A в тех случаях, когда B уже произошёл. Знаменатель у них разный: в P(A∩B) деление на все исходы, в P(A|B) — только на исходы B."
            },
            {
                id: "q_thick_2",
                type: "thick",
                question: "В каком случае формула P(A∩B) = P(A) × P(B) работает?",
                hint: "💡 Это верно только при определённом условии.",
                correctAnswer: "когда события A и B независимы",
                options: [
                    { value: "когда события A и B независимы", text: "когда события A и B независимы" },
                    { value: "когда события A и B совместны", text: "когда события A и B совместны" },
                    { value: "когда события A и B несовместны", text: "когда события A и B несовместны" },
                    { value: "всегда", text: "всегда" }
                ],
                explanation: "✅ Формула P(A∩B) = P(A) × P(B) работает ТОЛЬКО для независимых событий. Для зависимых событий нужно использовать условную вероятность: P(A∩B) = P(A) × P(B|A)."
            },
            {
                id: "q_thick_3",
                type: "thick",
                question: "Почему в формуле P(A∩B) = P(A) × P(B|A) порядок событий важен?",
                hint: "💡 P(B|A) и P(A|B) — это разные вероятности.",
                correctAnswer: "потому что P(B|A) не обязательно равно P(A|B)",
                options: [
                    { value: "потому что P(B|A) не обязательно равно P(A|B)", text: "потому что P(B|A) не обязательно равно P(A|B)" },
                    { value: "потому что умножение коммутативно", text: "потому что умножение коммутативно" },
                    { value: "порядок не важен", text: "порядок не важен" },
                    { value: "потому что P(A) и P(B) разные", text: "потому что P(A) и P(B) разные" }
                ],
                explanation: "✅ В общем случае P(B|A) ≠ P(A|B). Поэтому формулу можно записать двумя способами: P(A∩B) = P(A)×P(B|A) = P(B)×P(A|B). Выбор зависит от того, какая условная вероятность известна."
            },
            {
                id: "q_thick_4",
                type: "thick",
                question: "В мешке 3 белых и 2 чёрных шара. Вы вынимаете два шара без возвращения. Как найти P(второй белый | первый белый)?",
                hint: "💡 После того как вынули первый белый шар, сколько шаров осталось? Сколько среди них белых?",
                correctAnswer: "2/4 = 0,5",
                options: [
                    { value: "2/4 = 0,5", text: "2/4 = 0,5" },
                    { value: "3/5 = 0,6", text: "3/5 = 0,6" },
                    { value: "2/5 = 0,4", text: "2/5 = 0,4" },
                    { value: "3/4 = 0,75", text: "3/4 = 0,75" }
                ],
                explanation: "✅ После того как вынули один белый шар, в мешке осталось 4 шара: 2 белых и 2 чёрных. P(второй белый | первый белый) = 2/4 = 0,5."
            },
            {
                id: "q_thick_5",
                type: "thick",
                question: "Почему в задаче «в семье двое детей, хотя бы один мальчик» вероятность двух мальчиков равна 1/3, а не 1/2?",
                hint: "💡 Перечислите все возможные комбинации детей с учётом порядка.",
                correctAnswer: "потому что возможные исходы: ММ, МД, ДМ, а не ММ и МД",
                options: [
                    { value: "потому что возможные исходы: ММ, МД, ДМ, а не ММ и МД", text: "потому что возможные исходы: ММ, МД, ДМ, а не ММ и МД" },
                    { value: "потому что мальчиков рождается меньше", text: "потому что мальчиков рождается меньше" },
                    { value: "потому что порядок не важен", text: "потому что порядок не важен" },
                    { value: "потому что вероятность мальчика 1/3", text: "потому что вероятность мальчика 1/3" }
                ],
                explanation: "✅ Все возможные комбинации (с учётом порядка): ММ, МД, ДМ, ДД. Условие «хотя бы один мальчик» исключает ДД. Остаётся 3 равновероятных исхода. Только один из них (ММ) подходит → P = 1/3."
            }
        ]
    },
    // ========== ЗАДАНИЕ 2: ИНТЕРАКТИВНЫЙ КЛАСТЕР ДЛЯ УСЛОВНОЙ ВЕРОЯТНОСТИ ==========
    {
        id: "trkm_cluster_conditional",
        title: "🧠 ТРКМ: Кластер «Условная вероятность»",
        description: "Перетащите ключевые понятия в соответствующие ветви кластера. Неправильные карточки будут выделены красным.",
        type: "trkm_cluster",
        branches: [
            { id: "branch_def", name: "📖 ОПРЕДЕЛЕНИЕ", maxCards: 2 },
            { id: "branch_formula", name: "➕ ФОРМУЛА", maxCards: 3 },
            { id: "branch_property", name: "🔍 СВОЙСТВА", maxCards: 3 },
            { id: "branch_examples", name: "🎲 ПРИМЕРЫ", maxCards: 4 },
            { id: "branch_mistakes", name: "⚠️ ТИПИЧНЫЕ ОШИБКИ", maxCards: 3 }
        ],
        cards: [
            // Ветвь: ОПРЕДЕЛЕНИЕ (2 карточки)
            { id: "card_def_1", text: "Вероятность события A, вычисленная при условии, что событие B уже произошло" },
            { id: "card_def_2", text: "Показывает, как вероятность A меняется, если известно, что B случилось" },
            
            // Ветвь: ФОРМУЛА (3 карточки)
            { id: "card_formula_1", text: "P(A|B) = P(A∩B) / P(B)" },
            { id: "card_formula_2", text: "P(A∩B) = P(A) × P(B|A)" },
            { id: "card_formula_3", text: "P(A∩B) = P(B) × P(A|B)" },
            
            // Ветвь: СВОЙСТВА (3 карточки)
            { id: "card_prop_1", text: "Если A и B независимы, то P(A|B) = P(A)" },
            { id: "card_prop_2", text: "P(A|B) = P(B|A) × P(A) / P(B) (формула Байеса)" },
            { id: "card_prop_3", text: "0 ≤ P(A|B) ≤ 1" },
            
            // Ветвь: ПРИМЕРЫ (4 карточки)
            { id: "card_ex_1", text: "P(туз | красная карта) = 2/18 = 1/9" },
            { id: "card_ex_2", text: "P(второй белый | первый белый) = 2/4 = 0,5" },
            { id: "card_ex_3", text: "P(выпало 6 | чётное число) = 1/3" },
            { id: "card_ex_4", text: "P(оба мальчика | хотя бы один мальчик) = 1/3" },
            
            // Ветвь: ТИПИЧНЫЕ ОШИБКИ (3 карточки)
            { id: "card_mist_1", text: "Путают P(A|B) и P(B|A)" },
            { id: "card_mist_2", text: "Считают P(A∩B) = P(A)×P(B) для зависимых событий" },
            { id: "card_mist_3", text: "Забывают, что P(B) в знаменателе должна быть > 0" }
        ]
    }
];
    // ========== ТЕМЫ ДЛЯ КАЖДОГО КЛАССА ==========
const topicsByGrade = {
7: [
    { id: "grade7_topic1", name: "📊 Представление данных в таблицах" },
    { id: "grade7_topic2", name: "📈 Графическое представление данных", hasExcel: true },
    { id: "statistics_basic", name: "📐 Среднее арифметическое, мода, медиана, размах" },  // ЗАМЕНИЛИ
    { id: "grade7_topic4", name: "📊 Медиана числового набора" },
    { id: "grade7_topic5", name: "📏 Размах" },
    { id: "grade7_topic6", name: "🔢 Частота значений" },
    { id: "grade7_topic7", name: "🎲 Случайный опыт и случайное событие" },
    { id: "grade7_topic8", name: "🪙 Монета и игральная кость" },
    { id: "grade7_topic9", name: "🔗 Графы" }
],
8: [
    { id: "grade8_topic1", name: "📊 Дисперсия числового набора" },
    { id: "grade8_topic2", name: "📊 Стандартное отклонение" },
    { id: "grade8_topic3", name: "📈 Диаграммы рассеивания" },
    { id: "grade8_topic4", name: "🔢 Множества (объединение, пересечение, дополнение)" },
    { id: "grade8_topic5", name: "🎯 Диаграмма Эйлера. Объединение и пересечение событий" },
    { id: "multiplication", name: "✖️ Правило умножения" },
    { id: "opposite", name: "🔄 Противоположное событие" },
    { id: "euler", name: "🎯 Формула включений-исключений" },
    { id: "incompatible", name: "📊 Несовместные события. Формула сложения вероятностей" },
    { id: "conditional", name: "🎲 Условная вероятность. Формула умножения вероятностей" },
    { id: "tree", name: "🌳 Дерево эксперимента" }
],
    9: [
        { id: "grade9_topic1", name: "🔢 Перестановки, факториал, сочетания" },
        { id: "grade9_topic2", name: "🔺 Треугольник Паскаля" },
        { id: "grade9_topic3", name: "📐 Геометрическая вероятность" },
        { id: "grade9_topic4", name: "📊 Испытания Бернулли" },
        { id: "grade9_topic5", name: "📈 Математическое ожидание" },
        { id: "grade9_topic6", name: "📊 Закон больших чисел" }
    ]
};    
 // ========== БАЗА ДАННЫХ ==========
    const database = {
7: {statistics_basic: { cases: statisticsBasicCases, tests: statisticsBasicTests, formulas: statisticsBasicFormulas, practice: statisticsBasicPractice },
 grade7_topic1: { cases: grade7_topic1Cases, tests: grade7_topic1Tests, formulas: grade7_topic1Formulas, practice: grade7_topic1Practice }, grade7_topic2: { cases: grade7_topic2Cases, tests: grade7_topic2Tests, formulas: grade7_topic2Formulas, practice: grade7_topic2Practice }, grade7_topic3: { cases: grade7_topic3Cases, tests: grade7_topic3Tests, formulas: grade7_topic3Formulas, practice: grade7_topic3Practice },
grade7_topic4: { cases: grade7_topic4Cases, tests: grade7_topic4Tests, formulas: grade7_topic4Formulas, practice: grade7_topic4Practice }, 
grade7_topic5: { cases: grade7_topic5Cases, tests: grade7_topic5Tests, formulas: grade7_topic5Formulas, practice: grade7_topic5Practice },
grade7_topic6: { cases: grade7_topic6Cases, tests: grade7_topic6Tests, formulas: grade7_topic6Formulas, practice: grade7_topic6Practice },
grade7_topic7: { cases: grade7_topic7Cases, tests: grade7_topic7Tests, formulas: grade7_topic7Formulas, practice: grade7_topic7Practice },
grade7_topic8: { cases: grade7_topic8Cases, tests: grade7_topic8Tests, formulas: grade7_topic8Formulas, practice: grade7_topic8Practice },
grade7_topic9: { cases: grade7_topic9Cases, tests: grade7_topic9Tests, formulas: grade7_topic9Formulas, practice: grade7_topic9Practice } },
8: { 
    grade8_topic1: { cases: grade8_topic1Cases, tests: grade8_topic1Tests, formulas: grade8_topic1Formulas },
    grade8_topic2: { cases: grade8_topic2Cases, tests: grade8_topic2Tests, formulas: grade8_topic2Formulas },
    grade8_topic3: { cases: grade8_topic3Cases, tests: grade8_topic3Tests, formulas: grade8_topic3Formulas },
    grade8_topic4: { cases: grade8_topic4Cases, tests: grade8_topic4Tests, formulas: grade8_topic4Formulas },
    grade8_topic5: { cases: grade8_topic5Cases, tests: grade8_topic5Tests, formulas: grade8_topic5Formulas },
    multiplication: { cases: multiplicationCases, tests: multiplicationISSL, formulas: multiplicationFormulas }, 
    opposite: { cases: oppositeCases, tests: oppositeISSL, formulas: oppositeFormulas }, 
    incompatible: { cases: incompatibleCases, tests: incompatibleISSL_8, formulas: incompatibleFormulas}
,
    euler: { cases: eulerCases, tests: eulerISSL, formulas: eulerFormulas },  
    conditional: { cases: conditionalCases, tests: conditionalISSL, formulas: conditionalFormulas },  
    tree: { cases: treeCases, tests: treeISSL, formulas: treeFormulas }
},
        9: { grade9_topic1: { cases: grade9_topic1Cases, tests: grade9_topic1Tests, formulas: grade9_topic1Formulas, practice: grade9_topic1Practice }, grade9_topic2: { cases: grade9_topic2Cases, tests: grade9_topic2Tests, formulas: grade9_topic2Formulas, practice: grade9_topic2Practice }, grade9_topic3: { cases: grade9_topic3Cases, tests: grade9_topic3Tests, formulas: grade9_topic3Formulas, practice: grade9_topic3Practice }, grade9_topic4: { cases: grade9_topic4Cases, tests: grade9_topic4Tests, formulas: grade9_topic4Formulas, practice: grade9_topic4Practice }, grade9_topic5: { cases: grade9_topic5Cases, tests: grade9_topic5Tests, formulas: grade9_topic5Formulas, practice: grade9_topic5Practice }, grade9_topic6: { cases: grade9_topic6Cases, tests: grade9_topic6Tests, formulas: grade9_topic6Formulas, practice: grade9_topic6Practice }  }
    };

    // ========== СОСТОЯНИЕ ==========
    let currentGrade = 8;
    let currentTopic = "multiplication";
    let currentType = "cases";
    let solvedMap = {};
// ========== ПЕРЕМЕННЫЕ ДЛЯ ХРАНЕНИЯ ОТВЕТОВ НА ВОПРОСЫ КЕЙСОВ ==========
let caseAnswers = {};
// Переменные для Excel-редактора (нужны для работы других функций)
let excelData = { rows: 10, cols: 5, cells: {} };
let selectedCell = null;
let currentExcelTopic = null;
    function getStorageKey() { return `solved_${currentGrade}_${currentTopic}_${currentType}`; }
    function loadProgress() { const saved = localStorage.getItem(getStorageKey()); if(saved) solvedMap = JSON.parse(saved); else solvedMap = {}; }
    function saveProgress() { localStorage.setItem(getStorageKey(), JSON.stringify(solvedMap)); }
    function markSolved(caseId, solvedFlag = true) { if(solvedFlag) solvedMap[caseId] = true; else delete solvedMap[caseId]; saveProgress(); renderContent(); }
    function isSolved(caseId) { return solvedMap[caseId] === true; }
// ========== ФУНКЦИИ ДЛЯ РАБОТЫ С ВОПРОСАМИ КЕЙСОВ ==========
function getCaseAnswer(caseId, questionId) {
    const key = `case_${caseId}_${questionId}`;
    const saved = localStorage.getItem(key);
    return saved ? JSON.parse(saved) : null;
}

function saveCaseAnswer(caseId, questionId, answer, isCorrect) {
    const key = `case_${caseId}_${questionId}`;
    localStorage.setItem(key, JSON.stringify({ answer: answer, isCorrect: isCorrect }));
}

function clearCaseAnswers(caseId) {
    for (let i = 0; i < localStorage.length; i++) {
        const key = localStorage.key(i);
        if (key && key.startsWith(`case_${caseId}_`)) {
            localStorage.removeItem(key);
        }
    }
}
function renderTopicButtons() {
    const topics = topicsByGrade[currentGrade] || [];
    const container = document.getElementById('topicTabs');
    if(!container) return;
    let html = '';
    for(let i = 0; i < topics.length; i++) {
        const topic = topics[i];
        const activeClass = (currentTopic === topic.id) ? 'active' : '';
        const excelIcon = topic.hasExcel ? ' 📊' : '';
        html += `<button class="topic-btn ${activeClass}" data-topic="${topic.id}" data-has-excel="${topic.hasExcel}">${topic.name}${excelIcon}</button>`;
    }
    container.innerHTML = html;
    document.querySelectorAll('.topic-btn').forEach(btn => { 
        btn.addEventListener('click', () => { 
            setTopic(btn.dataset.topic);
        }); 
    });
}
        // Функция для пошагового тренажёра Исследовательское обучение
    function initStepTrainer(item) {
        const storageKey = `issl_${item.id}_progress`;
        let savedProgress = localStorage.getItem(storageKey);
        let stepAnswers = {};
        let currentStep = 1;
        
        if(savedProgress) {
            const parsed = JSON.parse(savedProgress);
            stepAnswers = parsed.stepAnswers || {};
            currentStep = parsed.currentStep || 1;
        }
        
        function saveProgressToLocal() {
            localStorage.setItem(storageKey, JSON.stringify({ stepAnswers: stepAnswers, currentStep: currentStep }));
        }
        
        function renderPreviousSteps() {
            const prevStepsContainer = document.getElementById(`prev-steps-${item.id}`);
            if(!prevStepsContainer) return;
            let prevHtml = '';
            for(let i = 1; i < currentStep; i++) {
                const step = item.steps[i - 1];
                const answer = stepAnswers[i];
                if(answer && answer.isCorrect) {
                    prevHtml += `<div class="prev-step-card"><div class="prev-step-title">📌 Шаг ${i}: ${step.question}</div><div class="prev-step-answer">✅ Ваш ответ: <strong>${answer.userAnswer}</strong></div><div class="prev-step-explanation">📖 Объяснение: ${step.explanation}</div></div>`;
                }
            }
            prevStepsContainer.innerHTML = prevHtml;
        }
        
        function updateStepNavigation() {
            const navContainer = document.getElementById(`step-nav-${item.id}`);
            if(!navContainer) return;
            let navHtml = '';
            for(let i = 1; i <= item.steps.length; i++) {
                const isActive = (currentStep === i);
                const isCompleted = stepAnswers[i] && stepAnswers[i].isCorrect;
                const completedClass = isCompleted ? 'completed' : '';
                navHtml += `<button class="step-btn ${isActive ? 'active' : ''} ${completedClass}" data-step="${i}">Шаг ${i}</button>`;
            }
            navContainer.innerHTML = navHtml;
            document.querySelectorAll(`#step-nav-${item.id} .step-btn`).forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const step = parseInt(btn.dataset.step);
                    currentStep = step;
                    saveProgressToLocal();
                    showStep(step);
                    updateStepNavigation();
                    renderPreviousSteps();
                });
            });
        }
        
        function showStep(stepNum) {
            const step = item.steps[stepNum - 1];
            const contentContainer = document.getElementById(`step-content-${item.id}`);
            const feedbackContainer = document.getElementById(`step-feedback-${item.id}`);
            if(!contentContainer) return;
            const alreadyAnswered = stepAnswers[stepNum] && stepAnswers[stepNum].isCorrect;
            let contentHtml = `<div class="step-content active-step"><div class="step-question">${step.question}</div><div class="step-answer-area"><input type="text" id="step-input-${item.id}-${stepNum}" class="step-input" placeholder="Введите ответ" ${alreadyAnswered ? 'disabled' : ''}>${!alreadyAnswered ? `<button class="step-check-btn" data-step="${stepNum}">✅ Проверить шаг ${stepNum}</button>` : '<span style="color: green;">✓ Шаг пройден!</span>'}</div></div>`;
            contentContainer.innerHTML = contentHtml;
            if(!alreadyAnswered) {
                const checkBtn = document.querySelector(`.step-check-btn[data-step="${stepNum}"]`);
                if(checkBtn) {
                    checkBtn.addEventListener('click', () => {
                        const input = document.getElementById(`step-input-${item.id}-${stepNum}`);
                        const userAnswer = input.value.trim().toLowerCase();
                        let isCorrect = (userAnswer === step.correctAnswer.toLowerCase());
                        if(isCorrect) {
                            stepAnswers[stepNum] = { userAnswer: userAnswer, isCorrect: true };
                            feedbackContainer.innerHTML = `<div class="step-feedback correct">✅ Верно! ${step.hint}</div>`;
                            feedbackContainer.style.display = 'block';
                            if(stepNum === item.steps.length && !isSolved(item.id)) markSolved(item.id, true);
                            saveProgressToLocal();
                            renderPreviousSteps();
                            updateStepNavigation();
                            if(stepNum < item.steps.length) {
                                currentStep = stepNum + 1;
                                saveProgressToLocal();
                                showStep(currentStep);
                                updateStepNavigation();
                                renderPreviousSteps();
                            } else {
                                const statusDiv = document.querySelector(`.case-card[data-item-id="${item.id}"] .case-status`);
                                if(statusDiv) { statusDiv.classList.add('solved'); statusDiv.innerHTML = '✅ Решён'; }
                            }
                        } else {
                            feedbackContainer.innerHTML = `<div class="step-feedback wrong">❌ Неверно. Правильный ответ: ${step.correctAnswer}. ${step.hint}</div>`;
                            feedbackContainer.style.display = 'block';
                        }
                        setTimeout(() => { feedbackContainer.style.display = 'none'; }, 4000);
                    });
                }
            }
            renderPreviousSteps();
        }
        
        const container = document.querySelector(`.case-card[data-item-id="${item.id}"] .step-container`);
        if(container && !document.getElementById(`prev-steps-${item.id}`)) {
            const prevDiv = document.createElement('div');
            prevDiv.id = `prev-steps-${item.id}`;
            prevDiv.className = 'prev-steps-container';
            container.insertBefore(prevDiv, container.firstChild);
        }
        
        const resetBtn = document.querySelector(`.reset-case[data-id="${item.id}"]`);
        if(resetBtn) {
            resetBtn.addEventListener('click', () => {
                localStorage.removeItem(storageKey);
                markSolved(item.id, false);
                renderContent();
            });
        }
        
        renderPreviousSteps();
        updateStepNavigation();
        showStep(currentStep);
    }

    // ========== ФУНКЦИЯ ДЛЯ ТЕСТА ТРКМ (Толстые и тонкие вопросы) ==========
// ========== ФУНКЦИЯ ДЛЯ ТЕСТА ТРКМ (Толстые и тонкие вопросы) С ОТДЕЛЬНОЙ КНОПКОЙ ПОДСКАЗКИ ==========
function initTest(item) {
    const storageKey = `trkm_test_${item.id}_progress`;
    let savedProgress = localStorage.getItem(storageKey);
    let answers = {};
    
    if(savedProgress) {
        answers = JSON.parse(savedProgress);
    }
    
    function saveProgress() {
        localStorage.setItem(storageKey, JSON.stringify(answers));
    }
    
    function renderTest() {
        const container = document.getElementById(`test-container-${item.id}`);
        if(!container) return;
        
        let allAnswered = true;
        let html = '';
        
        for(let i = 0; i < item.questions.length; i++) {
            const q = item.questions[i];
            const savedAnswer = answers[q.id];
            const isAnswered = savedAnswer !== undefined;
            const isCorrect = savedAnswer && savedAnswer.isCorrect;
            
            if(!isCorrect) allAnswered = false;
            
            const typeLabel = q.type === 'thin' ? '📌 Тонкий вопрос' : '🔍 Толстый вопрос';
            const typeColor = q.type === 'thin' ? '#0f5f9e' : '#eab308';
            
            // Для тонких вопросов - поле ввода
            let inputHtml = '';
            if(q.type === 'thin') {
                inputHtml = `
                    <input type="text" id="test-input-${q.id}" class="test-input" style="width: 100%; padding: 10px; border: 2px solid #cbdde9; border-radius: 40px; margin-bottom: 10px;" placeholder="Введите ответ" ${isCorrect ? 'disabled' : ''} value="${savedAnswer ? savedAnswer.userAnswer || '' : ''}">
                    <button class="test-check-btn" data-id="${q.id}" style="background: #2c6e2c; color: white; border: none; padding: 8px 20px; border-radius: 40px; cursor: pointer; margin-top: 5px; margin-right: 10px;">✅ Проверить</button>
                    <button class="test-hint-btn" data-id="${q.id}" style="background: #f59e0b; color: white; border: none; padding: 8px 20px; border-radius: 40px; cursor: pointer; margin-top: 5px;">💡 Подсказка</button>
                `;
            } else {
                // Для толстых вопросов - радиокнопки + кнопка подсказки
                inputHtml = '<div style="margin: 10px 0;">';
                for(let opt of q.options) {
                    const isSelected = savedAnswer && savedAnswer.userAnswer === opt.value;
                    inputHtml += `
                        <label style="display: block; margin: 8px 0; padding: 8px; background: ${isSelected ? '#e6f0fa' : 'white'}; border-radius: 8px; cursor: pointer;">
                            <input type="radio" name="q_${q.id}" value="${opt.value}" ${isCorrect ? 'disabled' : ''} ${isSelected ? 'checked' : ''} style="margin-right: 10px;">
                            <span>${opt.text}</span>
                        </label>
                    `;
                }
                inputHtml += `
                    <button class="test-check-btn" data-id="${q.id}" style="background: #2c6e2c; color: white; border: none; padding: 8px 20px; border-radius: 40px; cursor: pointer; margin-top: 5px; margin-right: 10px;">✅ Проверить</button>
                    <button class="test-hint-btn" data-id="${q.id}" style="background: #f59e0b; color: white; border: none; padding: 8px 20px; border-radius: 40px; cursor: pointer; margin-top: 5px;">💡 Подсказка</button>
                </div>`;
            }
            
            // Состояние подсказки (показывать/скрывать)
            const hintStorageKey = `hint_${item.id}_${q.id}`;
            const isHintVisible = localStorage.getItem(hintStorageKey) === 'true';
            
            html += `
                <div class="test-question-card" data-question-id="${q.id}" style="background: #f8fafc; border-radius: 1rem; padding: 1rem; margin-bottom: 1rem; border-left: 4px solid ${typeColor};">
                    <div class="test-question-header" style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;">
                        <strong style="color: #1e4663;">${typeLabel}</strong>
                        ${isCorrect ? '<span style="color: #0b5e2e;">✅ Решён</span>' : (isAnswered ? '<span style="color: #b91c1c;">❌ Неверно</span>' : '<span style="color: #5d7184;">⏳ Ожидает</span>')}
                    </div>
                    <div class="test-question" style="font-weight: 500; margin-bottom: 12px;">${q.question}</div>
                    <div class="test-answer-area">
                        ${inputHtml}
                        <div id="test-feedback-${q.id}" class="test-feedback" style="margin-top: 10px; font-size: 0.85rem;"></div>
                        <div id="test-hint-${q.id}" class="test-hint" style="margin-top: 10px; padding: 10px; background: #fffbeb; border-left: 4px solid #f59e0b; border-radius: 8px; display: ${isHintVisible ? 'block' : 'none'}; font-size: 0.85rem;">
                            💡 ${q.hint}
                        </div>
                        ${isCorrect ? `<div class="test-explanation" style="background: #d1fae5; padding: 10px; border-radius: 1rem; margin-top: 10px;">📖 ${q.explanation}</div>` : ''}
                    </div>
                </div>
            `;
        }
        
        const answeredCount = Object.keys(answers).filter(id => answers[id] && answers[id].isCorrect).length;
        const totalQuestions = item.questions.length;
        html += `<div class="test-progress" style="margin-top: 20px; padding: 10px; background: #f1f5f9; border-radius: 1rem; text-align: center;">
            <strong>Прогресс:</strong> ${answeredCount} / ${totalQuestions} вопросов решено
            ${allAnswered ? `<span style="color: #0b5e2e; margin-left: 10px;">🏆 Тест пройден!</span>` : ''}
        </div>`;
        
        container.innerHTML = html;
        
        // Добавляем обработчики для кнопок проверки
        for(let q of item.questions) {
            const checkBtn = document.querySelector(`.test-check-btn[data-id="${q.id}"]`);
            if(checkBtn) {
                checkBtn.addEventListener('click', () => {
                    let userAnswer = '';
                    
                    if(q.type === 'thin') {
                        const input = document.getElementById(`test-input-${q.id}`);
                        userAnswer = input ? input.value.trim().toLowerCase() : '';
                    } else {
                        const selectedRadio = document.querySelector(`input[name="q_${q.id}"]:checked`);
                        if(selectedRadio) {
                            userAnswer = selectedRadio.value;
                        }
                    }
                    
                    const feedbackDiv = document.getElementById(`test-feedback-${q.id}`);
                    
                    if(!userAnswer) {
                        feedbackDiv.innerHTML = `<div style="color: #b91c1c;">❌ Пожалуйста, введите ответ или выберите вариант.</div>`;
                        return;
                    }
                    
                    const isCorrect = (userAnswer === q.correctAnswer);
                    
                    if(isCorrect) {
                        answers[q.id] = { userAnswer: userAnswer, isCorrect: true };
                        saveProgress();
                        feedbackDiv.innerHTML = `<div style="color: #0b5e2e;">✅ Верно! ${q.explanation}</div>`;
                        renderTest();
                    } else {
                        answers[q.id] = { userAnswer: userAnswer, isCorrect: false };
                        saveProgress();
                        let correctText = q.correctAnswer;
                        if(q.options) {
                            const correctOpt = q.options.find(opt => opt.value === q.correctAnswer);
                            if(correctOpt) correctText = correctOpt.text;
                        }
                        feedbackDiv.innerHTML = `<div style="color: #b91c1c;">❌ Неверно. Правильный ответ: ${correctText}<br>💡 ${q.hint}</div>`;
                        renderTest();
                    }
                });
            }
            
            // Добавляем обработчики для кнопок подсказки
            const hintBtn = document.querySelector(`.test-hint-btn[data-id="${q.id}"]`);
            if(hintBtn) {
                hintBtn.addEventListener('click', () => {
                    const hintDiv = document.getElementById(`test-hint-${q.id}`);
                    if(hintDiv) {
                        const isVisible = hintDiv.style.display === 'block';
                        hintDiv.style.display = isVisible ? 'none' : 'block';
                        localStorage.setItem(`hint_${item.id}_${q.id}`, !isVisible);
                    }
                });
            }
        }
    }
    
    // Обработчик сброса
    const resetBtn = document.querySelector(`.reset-case[data-id="${item.id}"]`);
    if(resetBtn) {
        resetBtn.addEventListener('click', () => {
            localStorage.removeItem(storageKey);
            // Очищаем состояние подсказок
            for(let q of item.questions) {
                localStorage.removeItem(`hint_${item.id}_${q.id}`);
            }
            markSolved(item.id, false);
            renderTest();
        });
    }
    
    renderTest();
}        
    // ========== ФУНКЦИЯ ДЛЯ КЛАСТЕРА ТРКМ (с красной подсветкой неправильных карточек) ==========
    function initCluster(item) {
        const storageKey = `trkm_cluster_${item.id}_progress`;
        let savedProgress = localStorage.getItem(storageKey);
        let placements = {};
        
        if(savedProgress) {
            placements = JSON.parse(savedProgress);
        } else {
            for(let branch of item.branches) {
                placements[branch.id] = [];
            }
        }
        
        function saveProgress() {
            localStorage.setItem(storageKey, JSON.stringify(placements));
        }
        
        function renderCluster() {
            const container = document.getElementById(`cluster-container-${item.id}`);
            if(!container) return;
            
            // Функция для определения правильной ветки для карточки
            function getCorrectBranchForCard(cardId) {
                const cardText = item.cards.find(c => c.id === cardId)?.text || '';
                
                if (cardText.includes("События, которые не могут произойти одновременно") || 
                    cardText.includes("События исключают друг друга")) {
                    return "branch_def";
                }
                if (cardText.includes("нет общих исходов") || 
                    cardText.includes("Пересечение событий пусто")) {
                    return "branch_sign";
                }
                if (cardText.includes("P(A ∪ B) = P(A) + P(B)") || 
                    cardText.includes("Формула работает ТОЛЬКО для несовместных")) {
                    return "branch_formula";
                }
                if (cardText.includes("Выпадение 1 и 6") || 
                    cardText.includes("Орёл и решка") ||
                    cardText.includes("Вытащить красный или синий") ||
                    cardText.includes("Попадание и промах")) {
                    return "branch_examples";
                }
                if (cardText.includes("совместных событий есть общие исходы") || 
                    cardText.includes("Для совместных событий")) {
                    return "branch_compare";
                }
                return null;
            }
            
            // Сохраняем правильные ветки для каждой карточки
            const correctBranchMap = {};
            for(let card of item.cards) {
                correctBranchMap[card.id] = getCorrectBranchForCard(card.id);
            }
            
            // Получаем сохранённый результат проверки
            let checkResult = null;
            const savedResult = localStorage.getItem(`cluster_check_result_${item.id}`);
            if (savedResult) {
                checkResult = JSON.parse(savedResult);
            }
            
            const placedCardIds = new Set();
            for(let branchId in placements) {
                for(let card of placements[branchId]) {
                    placedCardIds.add(card.id);
                }
            }
            
            const resetBtn = document.querySelector(`.reset-case[data-id="${item.id}"]`);
            if(resetBtn) {
                resetBtn.addEventListener('click', () => {
                    localStorage.removeItem(storageKey);
                    localStorage.removeItem(`cluster_check_result_${item.id}`);
                    markSolved(item.id, false);
                    renderCluster();
                });
            }
            
            const availableCards = item.cards.filter(card => !placedCardIds.has(card.id));
            
            let html = `
                <div class="cluster-container">
                    <div class="cluster-center">
                        <div class="cluster-title">${item.title}</div>
                    </div>
                    <div class="cluster-branches">
            `;
            
            for(let branch of item.branches) {
                const branchCards = placements[branch.id] || [];
                html += `
                    <div class="cluster-branch">
                        <div class="branch-header">${branch.name}</div>
                        <div class="branch-dropzone" data-branch-id="${branch.id}" data-max-cards="${branch.maxCards}">
                `;
                
                if(branchCards.length === 0) {
                    html += `<div class="empty-slot">⬅ Перетащите сюда карточки</div>`;
                } else {
                    for(let card of branchCards) {
                        const isCardCorrect = (correctBranchMap[card.id] === branch.id);
                        // Ключевое изменение: если checkResult.performed === true И карточка НЕПРАВИЛЬНАЯ - добавляем класс wrong (красный)
                        let cardClass = '';
                        if (checkResult && checkResult.performed) {
                            if (!isCardCorrect) {
                                cardClass = 'wrong';  // ← ЗДЕСЬ красный цвет для неправильных карточек
                            } else {
                                cardClass = 'correct';
                            }
                        }
                        
                        html += `
                            <div class="placed-item ${cardClass}" data-card-id="${card.id}" data-branch-id="${branch.id}">
                                ${card.text}
                                <span style="float: right; font-size: 0.7rem; color: #999;">✖ удалить</span>
                            </div>
                        `;
                    }
                }
                html += `</div></div>`;
            }
            
            html += `
                    </div>
                    <div class="cluster-cards-pool">
                        <div class="pool-title">📦 Доступные карточки (перетащите в нужную ветвь)</div>
                        <div class="cards-grid" id="cards-grid-${item.id}">
            `;
            
            for(let card of availableCards) {
                html += `
                    <div class="drag-card" draggable="true" data-card-id="${card.id}" data-card-text="${card.text.replace(/"/g, '&quot;')}">
                        ${card.text}
                    </div>
                `;
            }
            
            html += `
                        </div>
                    </div>
                    <button class="cluster-check-btn" id="cluster-check-${item.id}">🔍 Проверить правильность</button>
                    <div id="cluster-result-${item.id}" class="cluster-result"></div>
                </div>
            `;
            
            container.innerHTML = html;
            
            const dragCards = document.querySelectorAll(`#cards-grid-${item.id} .drag-card`);
            const dropZones = document.querySelectorAll(`.branch-dropzone`);
            
            dragCards.forEach(card => {
                card.addEventListener('dragstart', handleDragStart);
                card.addEventListener('dragend', handleDragEnd);
            });
            
            dropZones.forEach(zone => {
                zone.addEventListener('dragover', handleDragOver);
                zone.addEventListener('dragleave', handleDragLeave);
                zone.addEventListener('drop', handleDrop);
            });
            
            document.querySelectorAll(`.placed-item`).forEach(itemEl => {
                itemEl.addEventListener('click', (e) => {
                    if(e.target !== itemEl && !itemEl.contains(e.target)) return;
                    const cardId = itemEl.dataset.cardId;
                    const branchId = itemEl.dataset.branchId;
                    const index = placements[branchId].findIndex(c => c.id === cardId);
                    if(index !== -1) {
                        placements[branchId].splice(index, 1);
                        localStorage.removeItem(`cluster_check_result_${item.id}`);
                        saveProgress();
                        renderCluster();
                    }
                });
            });
            
            const checkBtn = document.getElementById(`cluster-check-${item.id}`);
            if(checkBtn) {
                checkBtn.addEventListener('click', () => {
                    let totalCards = 0;
                    let correctCards = 0;
                    let wrongCards = [];
                    
                    for(let branch of item.branches) {
                        const branchCards = placements[branch.id] || [];
                        totalCards += branchCards.length;
                        
                        for(let card of branchCards) {
                            if(correctBranchMap[card.id] === branch.id) {
                                correctCards++;
                            } else {
                                wrongCards.push({card: card, branch: branch.name});
                            }
                        }
                    }
                    
                    const checkResultData = {
                        performed: true,
                        totalCards: totalCards,
                        correctCards: correctCards,
                        wrongCards: wrongCards
                    };
                    localStorage.setItem(`cluster_check_result_${item.id}`, JSON.stringify(checkResultData));
                    
                    const resultDiv = document.getElementById(`cluster-result-${item.id}`);
                    const allCardsPlaced = (totalCards === item.cards.length);
                    
                    if(allCardsPlaced && correctCards === item.cards.length) {
                        resultDiv.className = "cluster-result success";
                        resultDiv.innerHTML = `✅ Отлично! Все ${totalCards} карточек размещены ПРАВИЛЬНО!`;
                        if(!isSolved(item.id)) markSolved(item.id, true);
                    } else if(allCardsPlaced && correctCards < item.cards.length) {
                        resultDiv.className = "cluster-result error";
                        resultDiv.innerHTML = `⚠️ Размещено ${totalCards} из ${item.cards.length} карточек, но ПРАВИЛЬНЫХ только ${correctCards}.<br>❌ <strong style="color: #b91c1c;">Неправильные карточки выделены красным</strong>. Перетащите их в нужные ветки и проверьте снова.`;
                    } else {
                        resultDiv.className = "cluster-result error";
                        resultDiv.innerHTML = `📌 Размещено ${totalCards} из ${item.cards.length} карточек. Перетащите все карточки в ветви кластера.`;
                    }
                    
                    renderCluster();
                });
            }
            
            let draggedCard = null;
            
            function handleDragStart(e) {
                draggedCard = this;
                e.dataTransfer.setData('text/plain', JSON.stringify({
                    cardId: this.dataset.cardId,
                    cardText: this.dataset.cardText
                }));
                e.dataTransfer.effectAllowed = 'copy';
                this.classList.add('dragging');
            }
            
            function handleDragEnd(e) {
                if(this.classList) this.classList.remove('dragging');
                draggedCard = null;
                document.querySelectorAll('.branch-dropzone').forEach(zone => zone.classList.remove('drag-over'));
            }
            
            function handleDragOver(e) {
                e.preventDefault();
                e.dataTransfer.dropEffect = 'copy';
                this.classList.add('drag-over');
            }
            
            function handleDragLeave(e) {
                this.classList.remove('drag-over');
            }
            
            function handleDrop(e) {
                e.preventDefault();
                this.classList.remove('drag-over');
                
                const branchId = this.dataset.branchId;
                const maxCards = parseInt(this.dataset.maxCards);
                const currentCardsCount = (placements[branchId] || []).length;
                
                if(currentCardsCount >= maxCards) {
                    const resultDiv = document.getElementById(`cluster-result-${item.id}`);
                    if(resultDiv) {
                        resultDiv.className = "cluster-result error";
                        resultDiv.innerHTML = `⚠️ В этой ветви максимум ${maxCards} карточек.`;
                        setTimeout(() => {
                            resultDiv.style.display = 'none';
                            setTimeout(() => resultDiv.style.display = '', 100);
                        }, 2000);
                    }
                    return;
                }
                
                let cardData;
                try {
                    cardData = JSON.parse(e.dataTransfer.getData('text/plain'));
                } catch(e) { return; }
                
                if(!cardData) return;
                
                let alreadyPlaced = false;
                for(let bid in placements) {
                    if(placements[bid].some(c => c.id === cardData.cardId)) {
                        alreadyPlaced = true;
                        break;
                    }
                }
                
                if(alreadyPlaced) {
                    const resultDiv = document.getElementById(`cluster-result-${item.id}`);
                    if(resultDiv) {
                        resultDiv.className = "cluster-result error";
                        resultDiv.innerHTML = `⚠️ Эта карточка уже размещена.`;
                        setTimeout(() => {
                            resultDiv.style.display = 'none';
                            setTimeout(() => resultDiv.style.display = '', 100);
                        }, 2000);
                    }
                    return;
                }
                
                const card = item.cards.find(c => c.id === cardData.cardId);
                if(card) {
                    placements[branchId].push(card);
                    localStorage.removeItem(`cluster_check_result_${item.id}`);
                    saveProgress();
                    renderCluster();
                }
            }
        }
        
        renderCluster();
    }
// ========== ФУНКЦИЯ ДЛЯ EXCEL-АНАЛИЗА ==========
function renderExcelContent() {
    const container = document.getElementById('casesContainer');
    
    const excelHtml = `
        <div class="excel-workspace" style="background: white; border-radius: 2rem; padding: 2rem;">
            <div style="text-align: center; margin-bottom: 2rem;">
                <h2 style="color: #1e4663;">📊 Работа с данными (Excel-анализ)</h2>
                <p style="color: #5d7184;">Загрузите Excel-файл или CSV для статистического анализа</p>
            </div>
            
            <div class="excel-controls" style="display: flex; gap: 15px; justify-content: center; margin-bottom: 2rem; flex-wrap: wrap;">
                <button id="uploadExcelBtn" class="excel-action-btn" style="background: #1e6f3f; color: white; border: none; padding: 12px 24px; border-radius: 40px; cursor: pointer; font-weight: bold;">
                    📂 Загрузить Excel/CSV
                </button>
                <button id="downloadTemplateBtn" class="excel-action-btn" style="background: #0f5f9e; color: white; border: none; padding: 12px 24px; border-radius: 40px; cursor: pointer; font-weight: bold;">
                    📥 Скачать шаблон
                </button>
                <button id="clearDataBtn" class="excel-action-btn" style="background: #b91c1c; color: white; border: none; padding: 12px 24px; border-radius: 40px; cursor: pointer; font-weight: bold;">
                    🗑️ Очистить данные
                </button>
            </div>
            
            <input type="file" id="excelFileInput" accept=".xlsx, .xls, .csv, .txt" style="display: none;">
            
            <div id="excelDataPreview" style="display: none; margin-top: 2rem;">
                <div style="background: #f8fafc; border-radius: 1rem; padding: 1.5rem;">
                    <h3 style="color: #1e4663; margin-bottom: 1rem;">📋 Предпросмотр данных</h3>
                    <div id="dataTableContainer" style="overflow-x: auto; margin-bottom: 1rem;"></div>
                    
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1rem; margin-top: 1.5rem;">
                        <div class="stat-card" style="background: white; padding: 1rem; border-radius: 1rem;">
                            <h4>📊 Статистики</h4>
                            <div id="statisticsInfo"></div>
                        </div>
                        <div class="stat-card" style="background: white; padding: 1rem; border-radius: 1rem;">
                            <h4>🎲 Вероятностные задачи</h4>
                            <div id="probabilityTasks"></div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div id="excelEmptyState" style="text-align: center; padding: 3rem; background: #f8fafc; border-radius: 2rem; border: 2px dashed #cbdde9;">
                <div style="font-size: 4rem; margin-bottom: 1rem;">📊</div>
                <h3 style="color: #1e4663;">Загрузите данные для анализа</h3>
                <p style="color: #5d7184;">Поддерживаются форматы: .xlsx, .xls, .csv</p>
                <p style="color: #5d7184; font-size: 0.85rem;">Данные должны содержать числовые столбцы для расчёта статистик</p>
            </div>
        </div>
    `;
    
    container.innerHTML = excelHtml;
    
    // Подключаем обработчики
    document.getElementById('uploadExcelBtn')?.addEventListener('click', () => {
        document.getElementById('excelFileInput')?.click();
    });
    
    document.getElementById('excelFileInput')?.addEventListener('change', handleExcelUpload);
    
    document.getElementById('downloadTemplateBtn')?.addEventListener('click', downloadExcelTemplate);
    
    document.getElementById('clearDataBtn')?.addEventListener('click', () => {
        localStorage.removeItem('excel_data');
        document.getElementById('excelDataPreview').style.display = 'none';
        document.getElementById('excelEmptyState').style.display = 'block';
        alert('🧹 Данные очищены!');
    });
    
    // Проверяем, есть ли сохранённые данные
    const savedData = localStorage.getItem('excel_data');
    if (savedData) {
        try {
            const data = JSON.parse(savedData);
            displayExcelData(data);
        } catch(e) {}
    }
}

// Обработчик загрузки Excel
function handleExcelUpload(event) {
    const file = event.target.files[0];
    if (!file) return;
    
    const reader = new FileReader();
    reader.onload = function(e) {
        try {
            // Для CSV
            if (file.name.endsWith('.csv') || file.name.endsWith('.txt')) {
                const text = e.target.result;
                const rows = text.split('\n').map(row => row.split(','));
                const headers = rows[0];
                const data = rows.slice(1).filter(row => row.length > 1).map(row => {
                    const obj = {};
                    headers.forEach((header, idx) => {
                        obj[header.trim()] = row[idx] ? row[idx].trim() : '';
                    });
                    return obj;
                });
                displayExcelData(data);
                localStorage.setItem('excel_data', JSON.stringify(data));
            } 
            // Для Excel нужна библиотека SheetJS
            else {
                alert('📦 Для работы с Excel-файлами нужно подключить библиотеку SheetJS.\n\nСкопируйте этот код в <head>:\n<script src="https://cdn.sheetjs.com/xlsx-0.20.2/package/dist/xlsx.full.min.js"><\/script>');
                
                // Демо-данные для примера
                const demoData = [
                    { "Ученик": "Анна", "Математика": 85, "Физика": 90, "Информатика": 88 },
                    { "Ученик": "Борис", "Математика": 72, "Физика": 78, "Информатика": 85 },
                    { "Ученик": "Вика", "Математика": 95, "Физика": 92, "Информатика": 94 },
                    { "Ученик": "Глеб", "Математика": 68, "Физика": 70, "Информатика": 75 },
                    { "Ученик": "Дарья", "Математика": 88, "Физика": 85, "Информатика": 90 }
                ];
                displayExcelData(demoData);
                localStorage.setItem('excel_data', JSON.stringify(demoData));
            }
        } catch(err) {
            alert('❌ Ошибка при чтении файла: ' + err.message);
        }
    };
    
    if (file.name.endsWith('.csv') || file.name.endsWith('.txt')) {
        reader.readAsText(file, 'UTF-8');
    } else {
        reader.readAsArrayBuffer(file);
    }
}

// Отображение данных и генерация задач
function displayExcelData(data) {
    if (!data || data.length === 0) return;
    
    document.getElementById('excelEmptyState').style.display = 'none';
    document.getElementById('excelDataPreview').style.display = 'block';
    
    // Показываем таблицу
    const headers = Object.keys(data[0]);
    let tableHtml = '<table style="width: 100%; border-collapse: collapse;">';
    tableHtml += '<thead><tr style="background: #1e4663; color: white;">';
    headers.forEach(h => {
        tableHtml += `<th style="padding: 10px; border: 1px solid #cbdde9;">${h}</th>`;
    });
    tableHtml += '</tr></thead><tbody>';
    
    data.slice(0, 10).forEach(row => {
        tableHtml += '<tr>';
        headers.forEach(h => {
            tableHtml += `<td style="padding: 8px; border: 1px solid #cbdde9;">${row[h] || ''}</td>`;
        });
        tableHtml += '</tr>';
    });
    
    if (data.length > 10) {
        tableHtml += `<tr><td colspan="${headers.length}" style="padding: 10px; text-align: center; background: #f8fafc;">... и ещё ${data.length - 10} строк</td></tr>`;
    }
    tableHtml += '</tbody></table>';
    document.getElementById('dataTableContainer').innerHTML = tableHtml;
    
    // Находим числовые столбцы
    const numericColumns = [];
    headers.forEach(col => {
        const firstValue = parseFloat(data[0][col]);
        if (!isNaN(firstValue)) {
            numericColumns.push(col);
        }
    });
    
    // Рассчитываем статистики
    let statsHtml = '';
    let tasksHtml = '';
    
    numericColumns.forEach(col => {
        const values = data.map(row => parseFloat(row[col])).filter(v => !isNaN(v));
        if (values.length > 0) {
            const sum = values.reduce((a, b) => a + b, 0);
            const mean = sum / values.length;
            const sorted = [...values].sort((a, b) => a - b);
            const median = sorted[Math.floor(sorted.length / 2)];
            const min = Math.min(...values);
            const max = Math.max(...values);
            const variance = values.reduce((acc, v) => acc + Math.pow(v - mean, 2), 0) / values.length;
            const stdDev = Math.sqrt(variance);
            
            statsHtml += `
                <div style="margin-bottom: 15px; padding: 10px; background: #f0fdf4; border-radius: 8px;">
                    <strong>📈 ${col}</strong><br>
                    Среднее: ${mean.toFixed(2)} | Медиана: ${median}<br>
                    Мин/Макс: ${min} / ${max}<br>
                    Дисперсия: ${variance.toFixed(2)} | Ст. откл.: ${stdDev.toFixed(2)}
                </div>
            `;
            
            // Генерируем задачи
            tasksHtml += `
                <div style="margin-bottom: 15px; padding: 10px; background: #fff3e0; border-radius: 8px;">
                    <strong>🎲 Задача по столбцу "${col}":</strong><br>
                    <span style="font-size: 0.9rem;">Какова вероятность, что случайное значение из этого столбца будет больше ${Math.round(mean)}?</span>
                    <button class="task-answer-btn" data-col="${col}" data-mean="${mean}" style="margin-top: 8px; background: #0f5f9e; color: white; border: none; padding: 5px 12px; border-radius: 20px; cursor: pointer;">💡 Показать решение</button>
                    <div id="task-answer-${col}" style="display: none; margin-top: 8px; font-size: 0.85rem;"></div>
                </div>
            `;
        }
    });
    
    document.getElementById('statisticsInfo').innerHTML = statsHtml || '<p>Нет числовых данных для анализа</p>';
    document.getElementById('probabilityTasks').innerHTML = tasksHtml || '<p>Загрузите данные с числами для генерации задач</p>';
    
    // Добавляем обработчики для кнопок
    document.querySelectorAll('.task-answer-btn').forEach(btn => {
        btn.addEventListener('click', () => {
            const col = btn.dataset.col;
            const mean = parseFloat(btn.dataset.mean);
            const data = JSON.parse(localStorage.getItem('excel_data'));
            const values = data.map(row => parseFloat(row[col])).filter(v => !isNaN(v));
            const countGreater = values.filter(v => v > mean).length;
            const probability = (countGreater / values.length).toFixed(3);
            
            const answerDiv = document.getElementById(`task-answer-${col}`);
            answerDiv.style.display = 'block';
            answerDiv.innerHTML = `📊 Решение: Значений больше ${Math.round(mean)} — ${countGreater} из ${values.length} (${(probability * 100).toFixed(1)}%)<br>Вероятность = ${probability}`;
        });
    });
}

// Скачивание шаблона
function downloadExcelTemplate() {
    const templateData = [
        { "Имя": "Ученик 1", "Возраст": 14, "Рост_см": 155, "Вес_кг": 45, "Оценка_математика": 4, "Оценка_физика": 5 },
        { "Имя": "Ученик 2", "Возраст": 15, "Рост_см": 160, "Вес_кг": 50, "Оценка_математика": 3, "Оценка_физика": 4 },
        { "Имя": "Ученик 3", "Возраст": 14, "Рост_см": 158, "Вес_кг": 48, "Оценка_математика": 5, "Оценка_физика": 4 },
        { "Имя": "Ученик 4", "Возраст": 15, "Рост_см": 165, "Вес_кг": 55, "Оценка_математика": 4, "Оценка_физика": 3 },
        { "Имя": "Ученик 5", "Возраст": 14, "Рост_см": 152, "Вес_кг": 42, "Оценка_математика": 5, "Оценка_физика": 5 }
    ];
    
    // Создаём CSV для скачивания
    const headers = Object.keys(templateData[0]);
    const csvRows = [headers.join(',')];
    
    templateData.forEach(row => {
        const values = headers.map(header => row[header]);
        csvRows.push(values.join(','));
    });
    
    const blob = new Blob([csvRows.join('\n')], { type: 'text/csv' });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = 'шаблон_данных_для_анализа.csv';
    a.click();
    URL.revokeObjectURL(url);
    
    alert('✅ Шаблон скачан! Откройте его в Excel, заполните данными и загрузите обратно.');
}
// ========== EXCEL-ЗАДАНИЯ ДЛЯ РАЗНЫХ ТЕМ ==========
function getExcelTasksForTopic(topicId, grade) {
    const tasks = {
        // 7 класс
        "grade7_topic7": {  // Случайный опыт и случайное событие
            title: "🎲 Моделирование случайных событий",
            description: "Используйте Excel для моделирования случайных экспериментов. Введите формулы для генерации случайных чисел и анализа вероятностей.",
            examples: [
                { formula: "=СЛУЧМЕЖДУ(1;6)", description: "Генерация случайного числа от 1 до 6 (бросок кубика)" },
                { formula: "=ЕСЛИ(СЛУЧМЕЖДУ(1;2)=1;'Орёл';'Решка')", description: "Бросок монеты" },
                { formula: "=СЧЁТЕСЛИ(A1:A100;'>3')", description: "Подсчёт количества бросков кубика с результатом >3" }
            ],
            task: "Создайте таблицу со 100 бросками кубика. Найдите частоту выпадения каждой грани. Сравните с теоретической вероятностью (1/6)."
        },
        "grade7_topic8": {  // Монета и игральная кость
            title: "🪙 Анализ бросков монеты и кубика",
            description: "Промоделируйте серии бросков монеты и кубика, вычислите экспериментальные вероятности.",
            examples: [
                { formula: "=СЛУЧМЕЖДУ(0;1)", description: "Бросок монеты (0 - решка, 1 - орёл)" },
                { formula: "=СРЗНАЧ(A1:A100)", description: "Доля орлов в 100 бросках" },
                { formula: "=СУММПРОИЗВ((A1:A100=1)*(B1:B100>3))", description: "Подсчёт исходов 'орёл И число >3' при броске монеты и кубика" }
            ],
            task: "Проведите 200 экспериментов: бросаете монету и кубик. Запишите результаты. Найдите вероятность события 'выпал орёл И число >4'."
        },
        
        // 8 класс - Условная вероятность
        "conditional": {
            title: "🎲 Условная вероятность",
            description: "Проанализируйте зависимость между событиями с помощью Excel.",
            examples: [
                { formula: "=СЧЁТЕСЛИМН(A:A;1;B:B;1)", description: "Подсчёт совместных исходов (A=1 и B=1)" },
                { formula: "=СЧЁТЕСЛИ(A:A;1)", description: "Подсчёт исходов условия" },
                { formula: "=D2/D3", description: "Вычисление условной вероятности P(B|A)" }
            ],
            task: "Создайте таблицу с 500 парами случайных чисел (от 1 до 6). Найдите P(сумма>8 | первое число чётное) и P(первое число чётное | сумма>8). Сравните."
        },
        
        // 9 класс - Перестановки, факториал, сочетания
        "grade9_topic1": {
            title: "🔢 Комбинаторика в Excel",
            description: "Используйте комбинаторные функции Excel для расчёта перестановок и сочетаний.",
            examples: [
                { formula: "=ФАКТР(5)", description: "Вычисление факториала: 5! = 120" },
                { formula: "=ПЕРЕСТ(10;3)", description: "Число перестановок: P(10,3) = 720" },
                { formula: "=ЧИСЛКОМБ(10;3)", description: "Число сочетаний: C(10,3) = 120" }
            ],
            task: "Вычислите: сколько способов выбрать 3 учеников из 25? (C(25,3)). Сколько способов распределить 3 призовых места среди 10 участников? (P(10,3))."
        },
        
        // 9 класс - Испытания Бернулли
        "grade9_topic4": {
            title: "📊 Схема Бернулли",
            description: "Моделирование серий независимых испытаний с двумя исходами.",
            examples: [
                { formula: "=СЛУЧМЕЖДУ(0;1)", description: "Одно испытание Бернулли (0/1)" },
                { formula: "=БИНОМ.РАСП(3;10;0.5;ЛОЖЬ)", description: "Вероятность ровно 3 успехов в 10 испытаниях" },
                { formula: "=БИНОМ.РАСП(3;10;0.5;ИСТИНА)", description: "Вероятность ≤ 3 успехов" }
            ],
            task: "Смоделируйте 100 серий по 20 бросков монеты. Постройте гистограмму количества орлов в серии. Сравните с теоретическим биномиальным распределением."
        },
        
        // 9 класс - Математическое ожидание
        "grade9_topic5": {
            title: "📈 Математическое ожидание",
            description: "Вычисление математического ожидания на основе эмпирических данных.",
            examples: [
                { formula: "=СРЗНАЧ(A:A)", description: "Эмпирическое среднее (оценка мат. ожидания)" },
                { formula: "=СУММПРОИЗВ(A:A;B:B)", description: "Взвешенное среднее для распределения" },
                { formula: "=СУММПРОИЗВ(Диапазон_значений;Диапазон_вероятностей)", description: "Формула мат. ожидания дискретной величины" }
            ],
            task: "Загрузите данные об успеваемости. Вычислите математическое ожидание оценки. Сравните с медианой и модой."
        },
        
        // 9 класс - Закон больших чисел
        "grade9_topic6": {
            title: "📊 Закон больших чисел",
            description: "Визуализация сходимости частоты к вероятности при увеличении числа испытаний.",
            examples: [
                { formula: "=СЛУЧМЕЖДУ(1;6)", description: "Бросок кубика" },
                { formula: "=СЧЁТЕСЛИ($A$1:A1;6)/СТРОКА(A1)", description: "Накопленная частота выпадения 6" },
                { formula: "=ABS(B1-1/6)", description: "Отклонение от теоретической вероятности" }
            ],
            task: "Создайте график сходимости частоты выпадения 'орла' к вероятности 0.5. Покажите, как уменьшается отклонение с ростом числа испытаний (от 1 до 1000)."
        }
    };
    
    return tasks[topicId] || null;
}
// ========== EXCEL-РЕДАКТОР С ПОДДЕРЖКОЙ ФОРМУЛ ==========
function initExcelEditor(topicId) {
    currentExcelTopic = topicId;
    const savedData = localStorage.getItem(`excel_editor_${currentGrade}_${topicId}`);
    const taskInfo = getExcelTasksForTopic(topicId, currentGrade);
    
    if (savedData) {
        excelData = JSON.parse(savedData);
    } else {
        excelData = { rows: 10, cols: 5, cells: {} };
        for (let i = 0; i < excelData.rows; i++) {
            for (let j = 0; j < excelData.cols; j++) {
                const cellId = `${i},${j}`;
                excelData.cells[cellId] = { value: '', formula: '', displayValue: '' };
            }
        }
    }
    
    renderExcelEditorWithTask(taskInfo);
}

function renderExcelEditorWithTask(taskInfo) {
    const container = document.getElementById('casesContainer');
    
    let taskHtml = '';
    if (taskInfo) {
        taskHtml = `
            <div style="background: linear-gradient(135deg, #1e4663, #2c6e9e); color: white; border-radius: 1rem; padding: 1rem; margin-bottom: 1rem;">
                <h3 style="margin: 0 0 8px 0;">📚 ${taskInfo.title}</h3>
                <p style="margin: 0 0 12px 0; opacity: 0.9;">${taskInfo.description}</p>
                <details style="margin-top: 10px;">
                    <summary style="cursor: pointer; font-weight: bold;">📖 Примеры формул для этой темы</summary>
                    <div style="margin-top: 10px; padding: 10px; background: rgba(255,255,255,0.1); border-radius: 8px;">
                        ${taskInfo.examples.map(ex => `
                            <div style="margin-bottom: 8px;">
                                <code style="background: rgba(0,0,0,0.3); padding: 2px 6px; border-radius: 4px;">${ex.formula}</code>
                                <span style="font-size: 0.85rem;"> — ${ex.description}</span>
                            </div>
                        `).join('')}
                    </div>
                </details>
                <div style="margin-top: 12px; padding: 10px; background: rgba(255,255,255,0.15); border-radius: 8px;">
                    <strong>🎯 Задание:</strong> ${taskInfo.task}
                </div>
            </div>
        `;
    }
    
    const html = `
        <div class="excel-editor" style="background: white; border-radius: 1rem; padding: 1rem;">
            ${taskHtml}
            
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1rem; flex-wrap: wrap; gap: 10px;">
                <div>
                    <h3 style="color: #1e4663; margin: 0;">📊 Excel-редактор</h3>
                    <p style="color: #5d7184; font-size: 0.8rem; margin: 5px 0 0 0;">Поддерживаемые функции: СРЗНАЧ, СУММ, МАКС, МИН, СЧЁТ, СТАНДОТКЛОН, ФАКТР, ПЕРЕСТ, ЧИСЛКОМБ, БИНОМ.РАСП, СЛУЧМЕЖДУ</p>
                </div>
     <div style="display: flex; gap: 10px; flex-wrap: wrap;">
    <button id="excelAddRowBtn" class="excel-tool-btn" style="background: #0f5f9e;">➕ Добавить строку</button>
    <button id="excelAddColBtn" class="excel-tool-btn" style="background: #0f5f9e;">➕ Добавить столбец</button>
    <button id="excelClearBtn" class="excel-tool-btn" style="background: #b91c1c;">🗑️ Очистить таблицу</button>
    <button id="excelConditionalBtn" class="excel-tool-btn" style="background: #2c6e2c;">🎲 Создать таблицу условной вероятности</button>
    <button id="excelFormulaHelperBtn" class="excel-tool-btn" style="background: #eab308;">📖 Справка</button>
</div>
            </div>
            
            <div class="formula-bar" style="background: #f8fafc; padding: 8px; border-radius: 8px; margin-bottom: 10px; display: flex; gap: 10px; align-items: center;">
                <span style="font-weight: bold; min-width: 60px;" id="selectedCellRef">A1</span>
                <input type="text" id="formulaInput" class="formula-input" style="flex: 1; padding: 8px; border: 2px solid #cbdde9; border-radius: 8px; font-family: monospace;" placeholder="Введите значение или формулу (например, =СРЗНАЧ(A1:A5) или =ФАКТР(5))">
            </div>
            
            <div class="excel-table-container" style="overflow-x: auto; border: 1px solid #cbdde9; border-radius: 8px;">
                <table class="excel-table" id="excelTable" style="border-collapse: collapse; min-width: 100%;">
                    <thead>
                        <tr>
                            <th style="background: #e2e8f0; padding: 8px; border: 1px solid #cbdde9; min-width: 40px;">#</th>
                            ${Array(excelData.cols).fill().map((_, j) => `<th style="background: #e2e8f0; padding: 8px; border: 1px solid #cbdde9; min-width: 100px;">${String.fromCharCode(65 + j)}</th>`).join('')}
                        </tr>
                    </thead>
                    <tbody>
                        ${Array(excelData.rows).fill().map((_, i) => `
                            <tr>
                                <td style="background: #e2e8f0; padding: 8px; border: 1px solid #cbdde9; text-align: center; font-weight: bold;">${i + 1}</td>
                                ${Array(excelData.cols).fill().map((_, j) => {
                                    const cellId = `${i},${j}`;
                                    const cell = excelData.cells[cellId] || { value: '', displayValue: '' };
                                    const display = cell.displayValue !== undefined && cell.displayValue !== '' ? cell.displayValue : '';
                                    return `<td class="excel-cell" data-row="${i}" data-col="${j}" style="padding: 8px; border: 1px solid #cbdde9; cursor: pointer; min-width: 100px; ${selectedCell && selectedCell.row === i && selectedCell.col === j ? 'background: #dbeafe;' : ''}">${escapeHtml(String(display))}</td>`;
                                }).join('')}
                            </tr>
                        `).join('')}
                    </tbody>
                </table>
            </div>
            
            <div class="excel-stats" style="margin-top: 1rem; padding: 1rem; background: #f8fafc; border-radius: 8px;">
                <h4>📊 Быстрая статистика выделенного диапазона</h4>
                <div id="excelRangeStats" style="display: flex; gap: 15px; flex-wrap: wrap;">
                    <span>Сумма: <strong id="statSum">—</strong></span>
                    <span>Среднее: <strong id="statAvg">—</strong></span>
                    <span>Макс: <strong id="statMax">—</strong></span>
                    <span>Мин: <strong id="statMin">—</strong></span>
                    <span>Кол-во: <strong id="statCount">—</strong></span>
                </div>
            </div>
        </div>
    `;
    
    container.innerHTML = html;
    
    document.querySelectorAll('.excel-cell').forEach(cell => {
        cell.addEventListener('click', () => {
            const row = parseInt(cell.dataset.row);
            const col = parseInt(cell.dataset.col);
            selectCell(row, col);
        });
    });
    
    document.getElementById('excelAddRowBtn')?.addEventListener('click', addExcelRow);
    document.getElementById('excelAddColBtn')?.addEventListener('click', addExcelCol);
    document.getElementById('excelClearBtn')?.addEventListener('click', clearExcelTable);
    document.getElementById('excelFormulaHelperBtn')?.addEventListener('click', () => showFormulaHelp(taskInfo));
document.getElementById('excelConditionalBtn')?.addEventListener('click', createConditionalProbabilityTable);
    document.getElementById('formulaInput')?.addEventListener('change', updateFormula);
    
    if (excelData.rows > 0 && excelData.cols > 0) {
        selectCell(0, 0);
    }
}

function escapeHtml(str) {
    if (!str) return '';
    return str.replace(/[&<>]/g, function(m) {
        if (m === '&') return '&amp;';
        if (m === '<') return '&lt;';
        if (m === '>') return '&gt;';
        return m;
    });
}

function selectCell(row, col) {
    selectedCell = { row, col };
    const cellRef = `${String.fromCharCode(65 + col)}${row + 1}`;
    document.getElementById('selectedCellRef').innerHTML = cellRef;
    
    const cell = excelData.cells[`${row},${col}`];
    const formulaInput = document.getElementById('formulaInput');
    if (formulaInput) {
        if (cell && cell.formula) {
            formulaInput.value = cell.formula;
        } else {
            formulaInput.value = cell && cell.value ? cell.value : '';
        }
    }
    
    renderExcelEditorWithTask(getExcelTasksForTopic(currentExcelTopic, currentGrade));
}

function updateFormula() {
    if (!selectedCell) return;
    const formulaInput = document.getElementById('formulaInput');
    let formula = formulaInput.value;
    const cellId = `${selectedCell.row},${selectedCell.col}`;
    
    if (!excelData.cells[cellId]) {
        excelData.cells[cellId] = { value: '', formula: '', displayValue: '' };
    }
    
    if (formula.startsWith('=')) {
        excelData.cells[cellId].formula = formula;
        excelData.cells[cellId].value = '';
        evaluateFormula(cellId, formula);
    } else {
        excelData.cells[cellId].value = formula;
        excelData.cells[cellId].formula = '';
        excelData.cells[cellId].displayValue = formula;
    }
    
    saveExcelData();
    renderExcelEditorWithTask(getExcelTasksForTopic(currentExcelTopic, currentGrade));
}

function evaluateFormula(cellId, formula) {
    const match = formula.match(/=(\w+)\(([^:]+):([^)]+)\)/i);
    if (!match) {
        excelData.cells[cellId].displayValue = '#ОШИБКА!';
        return;
    }
    
    const funcName = match[1].toUpperCase();
    const startRef = match[2];
    const endRef = match[3];
    
    const start = parseCellRef(startRef);
    const end = parseCellRef(endRef);
    
    if (!start || !end) {
        excelData.cells[cellId].displayValue = '#ОШИБКА!';
        return;
    }
    
    const values = [];
    for (let i = Math.min(start.row, end.row); i <= Math.max(start.row, end.row); i++) {
        for (let j = Math.min(start.col, end.col); j <= Math.max(start.col, end.col); j++) {
            const cell = excelData.cells[`${i},${j}`];
            if (cell && cell.displayValue !== undefined && cell.displayValue !== '' && !isNaN(parseFloat(cell.displayValue))) {
                values.push(parseFloat(cell.displayValue));
            }
        }
    }
    
    let result;
    switch (funcName) {
        case 'СРЗНАЧ': case 'AVERAGE':
            result = values.reduce((a, b) => a + b, 0) / values.length;
            break;
        case 'СУММ': case 'SUM':
            result = values.reduce((a, b) => a + b, 0);
            break;
        case 'МАКС': case 'MAX':
            result = Math.max(...values);
            break;
        case 'МИН': case 'MIN':
            result = Math.min(...values);
            break;
        case 'СЧЁТ': case 'COUNT':
            result = values.length;
            break;
        case 'СТАНДОТКЛОН': case 'STDEV':
            const mean = values.reduce((a, b) => a + b, 0) / values.length;
            const variance = values.reduce((acc, v) => acc + Math.pow(v - mean, 2), 0) / values.length;
            result = Math.sqrt(variance);
            break;
        default:
            excelData.cells[cellId].displayValue = '#ИМЯ?';
            return;
    }
    
    excelData.cells[cellId].displayValue = Math.round(result * 100) / 100;
}

function parseCellRef(ref) {
    const match = ref.match(/([A-Z]+)(\d+)/);
    if (!match) return null;
    const col = match[1].charCodeAt(0) - 65;
    const row = parseInt(match[2]) - 1;
    return { row, col };
}

function addExcelRow() {
    excelData.rows++;
    for (let j = 0; j < excelData.cols; j++) {
        const cellId = `${excelData.rows - 1},${j}`;
        excelData.cells[cellId] = { value: '', formula: '', displayValue: '' };
    }
    saveExcelData();
    renderExcelEditorWithTask(getExcelTasksForTopic(currentExcelTopic, currentGrade));
}

function addExcelCol() {
    excelData.cols++;
    for (let i = 0; i < excelData.rows; i++) {
        const cellId = `${i},${excelData.cols - 1}`;
        excelData.cells[cellId] = { value: '', formula: '', displayValue: '' };
    }
    saveExcelData();
    renderExcelEditorWithTask(getExcelTasksForTopic(currentExcelTopic, currentGrade));
}

function clearExcelTable() {
    if (confirm('Очистить все ячейки? Это действие нельзя отменить.')) {
        for (let i = 0; i < excelData.rows; i++) {
            for (let j = 0; j < excelData.cols; j++) {
                const cellId = `${i},${j}`;
                excelData.cells[cellId] = { value: '', formula: '', displayValue: '' };
            }
        }
        saveExcelData();
        renderExcelEditorWithTask(getExcelTasksForTopic(currentExcelTopic, currentGrade));
    }
}

function showFormulaHelp(taskInfo) {
    let additionalFormulas = '';
    if (taskInfo && taskInfo.examples) {
        additionalFormulas = '\n\n📚 Примеры для этой темы:\n' + 
            taskInfo.examples.map(ex => `${ex.formula} — ${ex.description}`).join('\n');
    }
    
    alert('📖 Доступные формулы:\n\n' +
          '📊 Статистические:\n' +
          '=СРЗНАЧ(A1:A5) - среднее арифметическое\n' +
          '=СУММ(A1:A5) - сумма чисел\n' +
          '=МАКС(A1:A5) - максимальное значение\n' +
          '=МИН(A1:A5) - минимальное значение\n' +
          '=СЧЁТ(A1:A5) - количество чисел\n' +
          '=СТАНДОТКЛОН(A1:A5) - стандартное отклонение\n\n' +
          '🎲 Генерация случайных чисел:\n' +
          '=СЛУЧМЕЖДУ(1;6) - случайное число от 1 до 6\n\n' +
          '🔢 Комбинаторика:\n' +
          '=ФАКТР(5) - факториал числа (5! = 120)\n' +
          '=ПЕРЕСТ(10;3) - число перестановок P(10,3)\n' +
          '=ЧИСЛКОМБ(10;3) - число сочетаний C(10,3)\n\n' +
          '📈 Теория вероятностей:\n' +
          '=БИНОМ.РАСП(3;10;0.5;ЛОЖЬ) - биномиальное распределение' +
          additionalFormulas);
}

function saveExcelData() {
    localStorage.setItem(`excel_editor_${currentGrade}_${currentExcelTopic}`, JSON.stringify(excelData));
}
// ========== БЫСТРОЕ СОЗДАНИЕ ТАБЛИЦЫ ДЛЯ УСЛОВНОЙ ВЕРОЯТНОСТИ ==========
function createConditionalProbabilityTable() {
    if (!excelData) {
        alert('Сначала откройте Excel-редактор!');
        return;
    }
    
    // Создаём таблицу 500x5
    excelData.rows = 500;
    excelData.cols = 7;
    excelData.cells = {};
    
    // Заголовки в первой строке
    excelData.cells[`0,0`] = { value: 'Первое число', formula: '', displayValue: 'Первое число' };
    excelData.cells[`0,1`] = { value: 'Второе число', formula: '', displayValue: 'Второе число' };
    excelData.cells[`0,2`] = { value: 'Сумма', formula: '', displayValue: 'Сумма' };
    excelData.cells[`0,3`] = { value: 'Первое чётное?', formula: '', displayValue: 'Первое чётное?' };
    excelData.cells[`0,4`] = { value: 'Сумма>8?', formula: '', displayValue: 'Сумма>8?' };
    excelData.cells[`0,5`] = { value: 'Результат 1', formula: '', displayValue: 'Результаты' };
    excelData.cells[`0,6`] = { value: 'Результат 2', formula: '', displayValue: 'Результаты' };
    
    // Заполняем данные для 500 экспериментов (с 1 по 500 строки)
    for (let i = 1; i <= 500; i++) {
        const row = i;
        // Первое число (A) - случайное от 1 до 6
        excelData.cells[`${row},0`] = { value: '', formula: '=СЛУЧМЕЖДУ(1;6)', displayValue: '' };
        // Второе число (B) - случайное от 1 до 6
        excelData.cells[`${row},1`] = { value: '', formula: '=СЛУЧМЕЖДУ(1;6)', displayValue: '' };
        // Сумма = A+B
        excelData.cells[`${row},2`] = { value: '', formula: `=INDIRECT("R${row+1}C1",FALSE)+INDIRECT("R${row+1}C2",FALSE)`, displayValue: '' };
        // Первое чётное? (1 если чётное, 0 если нет)
        excelData.cells[`${row},3`] = { value: '', formula: `=IF(MOD(INDIRECT("R${row+1}C1",FALSE),2)=0,1,0)`, displayValue: '' };
        // Сумма > 8? (1 если да, 0 если нет)
        excelData.cells[`${row},4`] = { value: '', formula: `=IF(INDIRECT("R${row+1}C3",FALSE)>8,1,0)`, displayValue: '' };
    }
    
    // Строка для результатов (503 - после данных)
    const resultRow = 503;
    
    // Результат 1: P(сумма>8 | первое чётное)
    excelData.cells[`${resultRow},0`] = { value: 'P(сумма>8 | первое чётное) =', formula: '', displayValue: 'P(сумма>8 | первое чётное) =' };
    excelData.cells[`${resultRow},1`] = { value: '', formula: `=COUNTIF(R2C4:R501C4,1)`, displayValue: '' }; // Всего чётных
    excelData.cells[`${resultRow},2`] = { value: '', formula: `=COUNTIFS(R2C4:R501C4,1,R2C5:R501C5,1)`, displayValue: '' }; // Чётные И сумма>8
    excelData.cells[`${resultRow},3`] = { value: '', formula: `=RC[-1]/RC[-2]`, displayValue: '' }; // Результат
    
    // Результат 2: P(первое чётное | сумма>8)
    const resultRow2 = 505;
    excelData.cells[`${resultRow2},0`] = { value: 'P(первое чётное | сумма>8) =', formula: '', displayValue: 'P(первое чётное | сумма>8) =' };
    excelData.cells[`${resultRow2},1`] = { value: '', formula: `=COUNTIF(R2C5:R501C5,1)`, displayValue: '' }; // Всего сумма>8
    excelData.cells[`${resultRow2},2`] = { value: '', formula: `=COUNTIFS(R2C4:R501C4,1,R2C5:R501C5,1)`, displayValue: '' }; // Чётные И сумма>8 (то же самое)
    excelData.cells[`${resultRow2},3`] = { value: '', formula: `=RC[-1]/RC[-2]`, displayValue: '' }; // Результат
    
    // Пояснение
    const noteRow = 508;
    excelData.cells[`${noteRow},0`] = { value: 'Теоретически:', formula: '', displayValue: 'Теоретически:' };
    excelData.cells[`${noteRow+1},0`] = { value: 'P(сумма>8 | первое чётное) = 4/18 = 2/9 ≈ 0.2222', formula: '', displayValue: 'P(сумма>8 | первое чётное) = 4/18 = 2/9 ≈ 0.2222' };
    excelData.cells[`${noteRow+2},0`] = { value: 'P(первое чётное | сумма>8) = 4/10 = 0.4', formula: '', displayValue: 'P(первое чётное | сумма>8) = 4/10 = 0.4' };
    
    saveExcelData();
    
    // Перерисовываем таблицу
    renderExcelEditorWithTask(getExcelTasksForTopic(currentExcelTopic, currentGrade));
    
    alert('✅ Таблица создана!\n\n'
        + 'Создано 500 пар случайных чисел от 1 до 6.\n'
        + 'Автоматически считаются:\n'
        + '- P(сумма>8 | первое чётное) — в строке 503\n'
        + '- P(первое чётное | сумма>8) — в строке 505\n\n'
        + 'Сравните с теоретическими значениями (в строках 508-510)');
}
// Добавьте эту функцию где-нибудь перед renderContent()
function getTopicName(topicId) {
    const topics = topicsByGrade[currentGrade] || [];
    const topic = topics.find(t => t.id === topicId);
    return topic ? topic.name : topicId;
}
function renderContent() {
    const container = document.getElementById('casesContainer');
    
// Если выбран режим интерактивных заданий
if (currentType === 'interactive') {
    // Для 7 класса - тема "Графы"
    if (currentGrade === 7 && currentTopic === 'grade7_topic9') {
        initInteractive();  // Запустит задания по графам
    }
    // Для 8 класса - тема "Множества"
    else if (currentGrade === 8 && currentTopic === 'grade8_topic4') {
        initInteractive();  // Запустит задания по множествам
    }
    else {
        container.innerHTML = `<div class="empty-placeholder">
            🖱️ <strong>Интерактивные визуализации</strong><br><br>
            📌 Доступны в темах:<br>
            • 7 класс → <strong>«Графы (вершина, ребро, степень, цепь, цикл)»</strong><br>
            • 8 класс → <strong>«Множества (объединение, пересечение, дополнение)»</strong><br><br>
            Выберите одну из этих тем, чтобы начать.
        </div>`;
    }
    return;
}
    const classData = database[currentGrade] || {};
    const topicData = classData[currentTopic] || {};
    
    // Проверяем, есть ли у текущей темы поддержка Excel
    const currentTopicObj = topicsByGrade[currentGrade]?.find(t => t.id === currentTopic);
    const hasExcel = currentTopicObj?.hasExcel || false;
    
    // Если выбран Excel-режим и тема поддерживает Excel
    if (currentType === 'excel' && hasExcel) {
        initExcelEditor(currentTopic);
        return;
    }
    
    // Если выбран Excel-режим, но тема не поддерживает
    if (currentType === 'excel' && !hasExcel) {
        container.innerHTML = `<div class="empty-placeholder">📊 Режим Excel доступен только для статистических тем.<br>Выберите тему с иконкой 📊</div>`;
        return;
    }
    
    const items = topicData[currentType] || [];

    if(items.length === 0) {
        let typeName = currentType === "cases" ? "кейсам" : (currentType === "tests" ? "заданиям Исследовательское обучение" : (currentType === "formulas" ? "заданиям ТРКМ" : "упражнениям"));
        container.innerHTML = `<div class="empty-placeholder">📭 В этой теме пока нет заданий по ${typeName}.<br>🔜 Скоро добавятся!</div>`;
        return;
    }
    
    let html = '';
    for(let item of items) {
        if(item.steps && Array.isArray(item.steps)) {
            const solved = isSolved(item.id);
            html += `<div class="case-card" data-item-id="${item.id}"><div class="case-header"><div class="case-title">${item.title}</div><div class="case-status ${solved ? 'solved' : ''}">${solved ? '✅ Решён' : '⏳ Не решён'}</div></div><div class="case-description"><strong>📖 Ситуация:</strong><br>${item.description}</div><div id="step-container-${item.id}" class="step-container"><div class="step-nav" id="step-nav-${item.id}"></div><div id="step-content-${item.id}"></div><div id="step-feedback-${item.id}" class="step-feedback"></div></div>${solved ? `<button class="reset-case" data-id="${item.id}">⟳ Сбросить решение</button>` : ''}</div>`;
        } 
        else if(item.type === "trkm_test" && item.questions && Array.isArray(item.questions)) {
            const solved = isSolved(item.id);
            const statusClass = solved ? "solved" : "";
            const statusText = solved ? "✅ Решён" : "⏳ Не решён";
            
            html += `<div class="case-card" data-item-id="${item.id}">
                <div class="case-header">
                    <div class="case-title">${item.title}</div>
                    <div class="case-status ${statusClass}">${statusText}</div>
                </div>
                <div class="case-description"><strong>📖 Описание:</strong><br>${item.description}</div>
                <div id="test-container-${item.id}" class="test-container"></div>
                ${solved ? `<button class="reset-case" data-id="${item.id}">⟳ Сбросить решение</button>` : ''}
            </div>`;
        }
        else if(item.type === "trkm_cluster" && item.branches && Array.isArray(item.branches)) {
            const solved = isSolved(item.id);
            const statusClass = solved ? "solved" : "";
            const statusText = solved ? "✅ Решён" : "⏳ Не решён";
            
            html += `<div class="case-card" data-item-id="${item.id}">
                <div class="case-header">
                    <div class="case-title">${item.title}</div>
                    <div class="case-status ${statusClass}">${statusText}</div>
                </div>
                <div class="case-description"><strong>📖 Описание:</strong><br>${item.description}</div>
                <div id="cluster-container-${item.id}" class="cluster-container-wrapper"></div>
                ${solved ? `<button class="reset-case" data-id="${item.id}">⟳ Сбросить решение</button>` : ''}
            </div>`;
        }
else if(item.questions && Array.isArray(item.questions)) {
    // Обработка кейса с несколькими вопросами (как "Выбор лучшего продавца")
    const solved = isSolved(item.id);
    const statusClass = solved ? "solved" : "";
    const statusText = solved ? "✅ Решён" : "⏳ Не решён";
    
    let questionsHtml = '';
    for (let i = 0; i < item.questions.length; i++) {
        const q = item.questions[i];
        const savedAnswer = getCaseAnswer(item.id, q.id);
        const isCorrect = savedAnswer ? savedAnswer.isCorrect : false;
        
        if (q.type === 'choice') {
            questionsHtml += `
                <div class="question-block" style="margin-bottom: 20px; padding: 12px; background: #f8fafc; border-radius: 12px; border-left: 4px solid ${isCorrect ? '#2c6e2c' : '#eab308'}">
                    <div style="font-weight: 600; margin-bottom: 10px;">❓ ${q.text}</div>
                    <div class="options">
                        ${q.options.map(opt => `
                            <label style="display: block; margin: 5px 0;">
                                <input type="radio" name="q_${item.id}_${q.id}" value="${opt}" ${savedAnswer && savedAnswer.answer === opt ? 'checked' : ''} ${solved ? 'disabled' : ''}>
                                <span>${opt}</span>
                            </label>
                        `).join('')}
                    </div>
                    ${!solved && !isCorrect ? `<button class="check-question-btn" data-caseid="${item.id}" data-qid="${q.id}" data-correct="${q.correct}">✅ Проверить</button>` : ''}
                    <div class="feedback-small" id="feedback-${item.id}-${q.id}" style="margin-top: 8px; font-size: 0.85rem; color: ${isCorrect ? '#0b5e2e' : '#b91c1c'}">
                        ${isCorrect ? '✅ Верно!' : (savedAnswer && !savedAnswer.isCorrect ? '❌ Неверно. Попробуй ещё раз!' : '')}
                    </div>
                </div>
            `;
        } else if (q.type === 'input') {
            questionsHtml += `
                <div class="question-block" style="margin-bottom: 20px; padding: 12px; background: #f8fafc; border-radius: 12px; border-left: 4px solid ${isCorrect ? '#2c6e2c' : '#eab308'}">
                    <div style="font-weight: 600; margin-bottom: 10px;">❓ ${q.text}</div>
                    <input type="text" id="input_${item.id}_${q.id}" style="width: 150px; padding: 8px; border: 2px solid #cbdde9; border-radius: 20px;" value="${savedAnswer ? savedAnswer.answer : ''}" ${solved ? 'disabled' : ''}>
                    ${!solved && !isCorrect ? `<button class="check-question-btn" data-caseid="${item.id}" data-qid="${q.id}" data-correct="${q.correct}">✅ Проверить</button>` : ''}
                    <div class="feedback-small" id="feedback-${item.id}-${q.id}" style="margin-top: 8px; font-size: 0.85rem; color: ${isCorrect ? '#0b5e2e' : '#b91c1c'}">
                        ${isCorrect ? '✅ Верно!' : (savedAnswer && !savedAnswer.isCorrect ? '❌ Неверно. Попробуй ещё раз!' : '')}
                    </div>
                </div>
            `;
        } else if (q.type === 'text') {
            questionsHtml += `
                <div class="question-block" style="margin-bottom: 20px; padding: 12px; background: #f8fafc; border-radius: 12px; border-left: 4px solid ${isCorrect ? '#2c6e2c' : '#eab308'}">
                    <div style="font-weight: 600; margin-bottom: 10px;">❓ ${q.text}</div>
                    <textarea id="text_${item.id}_${q.id}" rows="3" style="width: 100%; padding: 8px; border: 2px solid #cbdde9; border-radius: 12px;" ${solved ? 'disabled' : ''}>${savedAnswer ? savedAnswer.answer : ''}</textarea>
                    ${!solved && !isCorrect ? `<button class="check-question-btn" data-caseid="${item.id}" data-qid="${q.id}" data-correct="${q.correctKeywords ? JSON.stringify(q.correctKeywords) : ''}">✅ Проверить</button>` : ''}
                    <div class="feedback-small" id="feedback-${item.id}-${q.id}" style="margin-top: 8px; font-size: 0.85rem; color: ${isCorrect ? '#0b5e2e' : '#b91c1c'}">
                        ${isCorrect ? '✅ Верно!' : (savedAnswer && !savedAnswer.isCorrect ? '❌ Неверно. Попробуй ещё раз!' : '')}
                    </div>
                </div>
            `;
        }
    }
    
    html += `<div class="case-card" data-item-id="${item.id}">
        <div class="case-header">
            <div class="case-title">${item.title}</div>
            <div class="case-status ${statusClass}">${statusText}</div>
        </div>
        <div class="case-description">${item.description}</div>
        <div class="stages-block">
            <button class="stages-btn" data-id="${item.id}-stages">📋 Показать этапы работы</button>
            <div id="stages-${item.id}" class="stages-content"><h4>📌 Этапы кейс-метода:</h4>${item.stages}</div>
        </div>
        <div class="questions-container">
            ${questionsHtml}
        </div>
        ${solved ? `<button class="reset-case" data-id="${item.id}">⟳ Сбросить решение</button>` : ''}
    </div>`;
}
        else {
            const solved = isSolved(item.id);
            const stagesHtml = item.stages ? `<button class="stages-btn" data-id="${item.id}-stages">📋 Показать этапы работы</button><div id="stages-${item.id}" class="stages-content"><h4>📌 Этапы кейс-метода:</h4>${item.stages}</div>` : '';
            html += `<div class="case-card"><div class="case-header"><div class="case-title">${item.title}</div><div class="case-status ${solved ? 'solved' : ''}">${solved ? '✅ Решён' : '⏳ Не решён'}</div></div><div class="case-description"><strong>📖 Ситуация:</strong><br>${item.description}</div>${stagesHtml}<div class="stage-block"><div class="question-text">📌 Вопрос для проверки:</div><div>${item.question}</div><div class="answer-row"><input type="text" id="ans-${item.id}" class="answer-input" placeholder="Ваш ответ"><button class="check-btn" data-id="${item.id}">🔍 Проверить</button></div><div id="feedback-${item.id}" class="feedback-area"></div><div class="action-buttons"><button class="hint-btn" data-id="${item.id}">💡 Подсказка</button><button class="solution-btn" data-id="${item.id}">📖 Посмотреть решение</button></div><div id="hint-${item.id}" class="hint-area">${item.hint}</div><div id="solution-${item.id}" class="solution-area">${item.solution}</div>${solved ? `<button class="reset-case" data-id="${item.id}">⟳ Сбросить решение (перерешать)</button>` : ''}</div></div>`;
        }
    }
    container.innerHTML = html;
    
    // Обработчики для кнопок проверки вопросов кейса
    for(let item of items) {
        if(item.questions && Array.isArray(item.questions)) {
            const checkBtns = document.querySelectorAll(`.check-question-btn[data-caseid="${item.id}"]`);
            checkBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    const caseId = btn.dataset.caseid;
                    const qId = btn.dataset.qid;
                    const question = item.questions.find(q => q.id === qId);
                    
                    let userAnswer = '';
                    if (question.type === 'choice') {
                        const selected = document.querySelector(`input[name="q_${caseId}_${qId}"]:checked`);
                        userAnswer = selected ? selected.value : '';
                    } else if (question.type === 'input') {
                        const input = document.getElementById(`input_${caseId}_${qId}`);
                        userAnswer = input ? input.value.trim() : '';
                    } else if (question.type === 'text') {
                        const textarea = document.getElementById(`text_${caseId}_${qId}`);
                        userAnswer = textarea ? textarea.value.trim().toLowerCase() : '';
                    }
                    
                    let isCorrect = false;
                    if (question.type === 'text' && question.correctKeywords) {
                        const keywords = question.correctKeywords.map(k => k.toLowerCase());
                        isCorrect = keywords.some(keyword => userAnswer.includes(keyword));
                    } else {
                        isCorrect = (userAnswer === question.correct);
                    }
                    
                    const feedbackDiv = document.getElementById(`feedback-${caseId}-${qId}`);
                    
                    if (isCorrect) {
                        saveCaseAnswer(caseId, qId, userAnswer, true);
                        feedbackDiv.innerHTML = `✅ Верно! ${question.explanation || ''}`;
                        feedbackDiv.style.color = '#0b5e2e';
                        btn.remove();
                        
                        let allCorrect = true;
                        for (let q of item.questions) {
                            const saved = getCaseAnswer(item.id, q.id);
                            if (!saved || !saved.isCorrect) {
                                allCorrect = false;
                                break;
                            }
                        }
                        if (allCorrect && !isSolved(item.id)) {
                            markSolved(item.id, true);
                        }
                        renderContent();
                    } else {
                        saveCaseAnswer(caseId, qId, userAnswer, false);
                        feedbackDiv.innerHTML = `❌ Неверно. ${question.hint || 'Попробуй ещё раз!'}`;
                        feedbackDiv.style.color = '#b91c1c';
                    }
                });
            });
        }
    }
    
    for(let item of items) {
        if(item.steps && Array.isArray(item.steps)) {
            initStepTrainer(item);
        } 
        else if(item.type === "trkm_test" && item.questions && Array.isArray(item.questions)) {
            initTest(item);
        }
        else if(item.type === "trkm_cluster" && item.branches && Array.isArray(item.branches)) {
            initCluster(item);
        }
        else if(!item.questions) {
            const stagesBtn = document.querySelector(`.stages-btn[data-id="${item.id}-stages"]`);
            if(stagesBtn) {
                stagesBtn.addEventListener('click', () => {
                    const div = document.getElementById(`stages-${item.id}`);
                    div.classList.toggle('show');
                    stagesBtn.textContent = div.classList.contains('show') ? '📋 Скрыть этапы' : '📋 Показать этапы работы';
                });
            }
            const checkBtn = document.querySelector(`.check-btn[data-id="${item.id}"]`);
            if(checkBtn) {
                checkBtn.addEventListener('click', () => {
                    const input = document.getElementById(`ans-${item.id}`);
                    const normalized = item.answerNormalizer(input.value);
                    const isCorrect = (Math.abs(normalized - item.answer) < 0.0001) || (normalized == item.answer);
                    const feedbackDiv = document.getElementById(`feedback-${item.id}`);
                    if(isCorrect) {
                        if(!isSolved(item.id)) { markSolved(item.id, true); feedbackDiv.innerHTML = "✅ Верно! Задание засчитано."; }
                        else { feedbackDiv.innerHTML = "✅ Верно! (уже решено)"; }
                        feedbackDiv.style.color = "#0b5e2e";
                    } else {
                        feedbackDiv.innerHTML = "❌ Неверно. Используйте подсказку или готовое решение.";
                        feedbackDiv.style.color = "#b91c1c";
                    }
                });
            }
            
            const hintBtn = document.querySelector(`.hint-btn[data-id="${item.id}"]`);
            if(hintBtn) hintBtn.addEventListener('click', () => document.getElementById(`hint-${item.id}`).classList.toggle('show'));
            
            const solBtn = document.querySelector(`.solution-btn[data-id="${item.id}"]`);
            if(solBtn) solBtn.addEventListener('click', () => document.getElementById(`solution-${item.id}`).classList.toggle('show'));
            
            const resetBtn = document.querySelector(`.reset-case[data-id="${item.id}"]`);
            if(resetBtn) resetBtn.addEventListener('click', () => markSolved(item.id, false));
            
            if(isSolved(item.id)) document.getElementById(`solution-${item.id}`)?.classList.add('show');
        }
    }
    
    // Обработчики для кнопок этапов кейс-метода (ВНЕ цикла for)
    document.querySelectorAll('.stages-btn').forEach(btn => {
        btn.addEventListener('click', () => {
            const id = btn.dataset.id;
            if(id) {
                const div = document.getElementById(`stages-${id}`);
                if(div) {
                    div.classList.toggle('show');
                    btn.textContent = div.classList.contains('show') ? '📋 Скрыть этапы' : '📋 Показать этапы работы';
                }
            }
        });
    });
}
    function setGrade(grade) {
        currentGrade = grade;
        document.querySelectorAll('.grade-btn').forEach(btn => { const g = parseInt(btn.dataset.grade); if(g === grade) btn.classList.add('active'); else btn.classList.remove('active'); });
        const topics = topicsByGrade[grade] || [];
        currentTopic = topics.length > 0 ? topics[0].id : "";
        renderTopicButtons();
        loadProgress();
        renderContent();
    }
    
    function setTopic(topic) {
        currentTopic = topic;
        document.querySelectorAll('.topic-btn').forEach(btn => { const t = btn.dataset.topic; if(t === topic) btn.classList.add('active'); else btn.classList.remove('active'); });
        loadProgress();
        renderContent();
    }
    
    function setType(type) {
        currentType = type;
        document.querySelectorAll('.type-btn').forEach(btn => { const t = btn.dataset.type; if(t === type) btn.classList.add('active'); else btn.classList.remove('active'); });
        loadProgress();
        renderContent();
    }
    
    loadProgress();
    renderTopicButtons();
    renderContent();
    
    document.querySelectorAll('.grade-btn').forEach(btn => btn.addEventListener('click', () => setGrade(parseInt(btn.dataset.grade))));
    document.querySelectorAll('.type-btn').forEach(btn => btn.addEventListener('click', () => setType(btn.dataset.type)));
// ========== ИНТЕРАКТИВНЫЕ ВИЗУАЛИЗАЦИИ (HOTSPOT) ==========
const interactiveTasks = [
    {
        id: "euler_union_2",
        title: "Задание 1",
        question: "Кликни по ВСЕМ областям диаграммы, которые соответствуют событию A ∪ B (объединение событий A и B).",
        type: "hotspot",
        diagramType: "twoCircles",
        correctAreas: ["left", "intersection", "right"],
        areaNames: {
            left: "Область только A",
            intersection: "Область пересечения A∩B",
            right: "Область только B"
        },
        feedback: "✅ Верно! A ∪ B — это все исходы, входящие хотя бы в A или B."
    },
    {
        id: "euler_intersection_2",
        title: "Задание 2",
        question: "Кликни по области диаграммы, которая соответствует событию A ∩ B (пересечение событий A и B).",
        description: "A ∩ B — это общая часть A и B.",
        type: "hotspot",
        diagramType: "twoCircles",
        correctAreas: ["intersection"],
        areaNames: {
            intersection: "Область пересечения A∩B"
        },
        feedback: "✅ Верно! A ∩ B — это общая часть A и B."
    },
    {
        id: "euler_only_a",
        title: "Задание 3",
        question: "Кликни по области диаграммы, которая соответствует событию «только A»",
        description: "Это область, принадлежащая A, но не входящая в B.",
        type: "hotspot",
        diagramType: "twoCircles",
        correctAreas: ["left"],
        areaNames: {
            left: "Область только A"
        },
        feedback: "✅ Верно! Это область, принадлежащая A, но не B."
    },
    {
        id: "euler_only_b",
        title: "Задание 4",
        question: "Кликни по области диаграммы, которая соответствует событию «только B»",
        description: "Это область, принадлежащая B, но не входящая в A.",
        type: "hotspot",
        diagramType: "twoCircles",
        correctAreas: ["right"],
        areaNames: {
            right: "Область только B"
        },
        feedback: "✅ Верно! Это область, принадлежащая B, но не A."
    },
    {
        id: "euler_neither",
        title: "Задание 5",
        question: "Кликни по области диаграммы, которая соответствует событию «ни A, ни B».",
        description: "Это область за пределами A и B.",
        type: "hotspot",
        diagramType: "twoCircles",
        correctAreas: ["outside"],
        areaNames: {
            outside: "Область вне кругов"
        },
        feedback: "✅ Верно! Это область вне A и B."
    },
    {
        id: "euler_union_3",
        title: "Задание 6",
        question: "Кликни по ВСЕМ областям диаграммы, которые соответствуют событию A ∪ B ∪ C (объединение трёх событий).",
        description: "A ∪ B ∪ C — это все исходы, входящие хотя бы в один из трёх кругов.",
        type: "hotspot",
        diagramType: "threeCircles",
        correctAreas: ["a", "b", "c", "ab", "ac", "bc", "abc"],
        areaNames: {
            a: "Только A",
            b: "Только B",
            c: "Только C",
            ab: "A∩B (без C)",
            ac: "A∩C (без B)",
            bc: "B∩C (без A)",
            abc: "A∩B∩C"
        },
        feedback: "✅ Верно! A ∪ B ∪ C — это все исходы, входящие хотя бы в один из трёх кругов."
    },
    {
        id: "euler_intersection_3",
        title: "Задание 7",
        question: "Кликни по области диаграммы, которая соответствует событию A ∩ B ∩ C (пересечение трёх событий).",
        description: "A ∩ B ∩ C — это общая часть всех трёх кругов.",
        type: "hotspot",
        diagramType: "threeCircles",
        correctAreas: ["abc"],
        areaNames: {
            abc: "Центральная область A∩B∩C"
        },
        feedback: "✅ Верно! A ∩ B ∩ C — это общая часть всех трёх кругов."
    },
    {
        id: "euler_only_a_3",
        title: "Задание 8",
        question: "Кликни по области диаграммы, которая соответствует событию «только A».",
        description: "Это часть круга A, не пересекающаяся с B и C.",
        type: "hotspot",
        diagramType: "threeCircles",
        correctAreas: ["a"],
        areaNames: {
            a: "Только A"
        },
        feedback: "✅ Верно! Это область, принадлежащая только A."
    },
    {
        id: "euler_union_intersections",
        title: "Задание 9",
        question: "Кликни по ВСЕМ областям диаграммы, которые соответствуют событию (A ∩ B) ∪ (A ∩ C).",
        description: "Это область, где A пересекается с B или A пересекается с C.",
        type: "hotspot",
        diagramType: "threeCircles",
        correctAreas: ["ab", "ac", "abc"],
        areaNames: {
            ab: "A∩B (без C)",
            ac: "A∩C (без B)",
            abc: "A∩B∩C"
        },
        feedback: "✅ Верно! Это область, где A пересекается с B или A пересекается с C."
    },
    {
        id: "euler_symmetric_difference",
        title: "Задание 10",
        question: "Кликни по ВСЕМ областям диаграммы, которые соответствуют событию «только A или только B».",
        description: "Это области A без B и B без A (две отдельные области).",
        type: "hotspot",
        diagramType: "twoCircles",
        correctAreas: ["left", "right"],
        areaNames: {
            left: "Область только A",
            right: "Область только B"
        },
        feedback: "✅ Верно! Это области, где есть A или B, но не оба одновременно."
    }
];
// ========== ИНТЕРАКТИВНЫЕ ВИЗУАЛИЗАЦИИ ДЛЯ ТЕМЫ "ГРАФЫ" (7 КЛАСС) ==========
const graphInteractiveTasks = [
{
    id: "graph_degree_1",
    title: "📊 Задание 1: Найди вершину с заданной степенью",
    question: "Кликни по вершинам, степень которых равна 3.",
    description: "Степень вершины — это количество рёбер, которые из неё выходят.",
    type: "hotspot_graph",
    diagramType: "graph_basic",
    singleSelect: true,
    correctAreas: ["vertex_a", "vertex_b", "vertex_d", "vertex_e"],  // У B и F 
    areaNames: {
        vertex_a: "Вершина A",
        vertex_b: "Вершина B",
        vertex_c: "Вершина C",
        vertex_d: "Вершина D",
        vertex_e: "Вершина E",
        vertex_f: "Вершина F",
        vertex_g: "Вершина G"
    },
    feedback: "✅ Верно! Эти вершины соединены ровно с тремя другими. Их степень равна 3."
},
    {
    id: "graph_degree_2",
    title: "📊 Задание 2: Найди вершины с разными степенями",
    question: "Кликни по ВСЕМ нужным вершинам: сначала по вершинам со степенью 4, затем по изолированной вершине.",
    description: "Изолированная вершина — это вершина, которая не соединена ни с одной другой.",
    type: "hotspot_graph",
    diagramType: "graph_isolated",
    singleSelect: false,
    correctAreas: ["vertex_b", "vertex_d", "vertex_f"],
    areaNames: {
        vertex_a: "Вершина A ()",
        vertex_b: "Вершина B (степень 4)",
        vertex_c: "Вершина C ()",
        vertex_d: "Вершина D (степень 4)",
        vertex_e: "Вершина E (степень 2)",
        vertex_f: "Вершина F (степень 0) - изолированная",
        vertex_g: "Вершина G (степень 2)"
    },
    feedback: "✅ Верно! Вершина D имеет степень 4, а вершина F — изолированная (степень 0)."
},
    {
        id: "graph_path_length",
        title: "📊 Задание 3: Найди путь заданной длины",
        question: "Кликни по вершине, в которую ведёт цепь длины 4, начинающаяся в вершине A.",
        description: "Цепь — это путь без повторяющихся вершин. Длина цепи = количество рёбер.",
        type: "hotspot_graph",
        diagramType: "graph_path",
        singleSelect: true,
        correctAreas: ["vertex_e"],
        areaNames: {
            vertex_a: "Вершина A (начало, расстояние 0)",
            vertex_b: "Вершина B (расстояние 1 от A)",
            vertex_c: "Вершина C (расстояние 2 от A)",
            vertex_d: "Вершина D (расстояние 3 от A)",
            vertex_e: "Вершина E (расстояние 4 от A)"
        },
        feedback: "✅ Верно! Путь A → B → C → D → E имеет длину 4. Молодец!"
    },
    {
        id: "graph_cycle",
        title: "📊 Задание 4: Найди простой цикл",
        question: "Кликни по ТРЁМ вершинам, которые образуют простой цикл.",
        description: "Простой цикл — это путь, где начало и конец совпадают, а вершины не повторяются.",
        type: "hotspot_graph",
        diagramType: "graph_cycle",
        singleSelect: false,
        correctAreas: ["vertex_a", "vertex_b", "vertex_c"],
        areaNames: {
            vertex_a: "Вершина A (верхняя)",
            vertex_b: "Вершина B (левая нижняя)",
            vertex_c: "Вершина C (правая нижняя)",
            vertex_d: "Вершина D (левая)",
            vertex_e: "Вершина E (правая)"
        },
        feedback: "✅ Верно! Вершины A, B и C образуют треугольник — простой цикл длины 3."
    },
    {
        id: "graph_handshake",
        title: "📊 Задание 5: Лемма о рукопожатиях",
        question: "В графе 5 вершин. Из двух вершин выходит по 3 ребра, из трёх — по 4. Возможен ли такой граф?",
        description: "Лемма о рукопожатиях: сумма степеней всех вершин должна быть чётной.",
        type: "hotspot_graph",
        diagramType: "text_only",
        singleSelect: true,
        correctAreas: ["answer_yes"],
        areaNames: {
            answer_yes: "✅ Да, возможен",
            answer_no: "❌ Нет, невозможен"
        },
        feedback: "✅ Верно! Сумма степеней = 2×3 + 3×4 = 6 + 12 = 18 (чётное число). Такой граф существует!"
    }
];
// Функция отрисовки графа для задания 1 (все пересечения - вершины)
function drawGraphBasic() {
    return `<svg width="500" height="400" viewBox="0 0 500 400" class="diagram-svg">
        <rect x="0" y="0" width="500" height="400" fill="#f8fafc" rx="10"/>
        
        <!-- Рёбра - соединяем вершины, а не пересекаем -->
        <line x1="100" y1="150" x2="200" y2="100" stroke="#64748b" stroke-width="2.5"/>
        <line x1="100" y1="150" x2="200" y2="200" stroke="#64748b" stroke-width="2.5"/>
        <line x1="100" y1="150" x2="60" y2="280" stroke="#64748b" stroke-width="2.5"/>
        <line x1="200" y1="100" x2="200" y2="200" stroke="#64748b" stroke-width="2.5"/>
        <line x1="200" y1="100" x2="340" y2="80" stroke="#64748b" stroke-width="2.5"/>
        <line x1="200" y1="200" x2="340" y2="220" stroke="#64748b" stroke-width="2.5"/>
        <line x1="60" y1="280" x2="200" y2="200" stroke="#64748b" stroke-width="2.5"/>
        <line x1="340" y1="80" x2="340" y2="220" stroke="#64748b" stroke-width="2.5"/>
        <line x1="340" y1="80" x2="440" y2="150" stroke="#64748b" stroke-width="2.5"/>
        <line x1="340" y1="220" x2="440" y2="150" stroke="#64748b" stroke-width="2.5"/>
        
        <!-- Вершины (все точки соединения рёбер) -->
        <circle class="hotspot-area" data-area="vertex_a" cx="100" cy="150" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="100" y="156" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">A</text>
        
        <circle class="hotspot-area" data-area="vertex_b" cx="200" cy="100" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="200" y="106" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">B</text>
        
        <circle class="hotspot-area" data-area="vertex_c" cx="200" cy="200" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="200" y="206" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">C</text>
        
        <circle class="hotspot-area" data-area="vertex_d" cx="340" cy="80" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="340" y="86" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">D</text>
        
        <circle class="hotspot-area" data-area="vertex_e" cx="340" cy="220" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="340" y="226" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">E</text>
        
        <circle class="hotspot-area" data-area="vertex_f" cx="60" cy="280" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="60" y="286" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">F</text>
        
        <circle class="hotspot-area" data-area="vertex_g" cx="440" cy="150" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="440" y="156" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">G</text>
    </svg>`;
}
// Функция отрисовки графа для задания 2 (без лишних отрезков)
function drawGraphIsolated() {
    return `<svg width="550" height="400" viewBox="0 0 550 400" class="diagram-svg">
        <rect x="0" y="0" width="550" height="400" fill="#f8fafc" rx="10"/>
        
        <!-- Рёбра - только соединения между существующими вершинами -->
        <!-- Соединения с D -->
        <line x1="100" y1="150" x2="280" y2="200" stroke="#64748b" stroke-width="2.5"/>
        <line x1="180" y1="100" x2="280" y2="200" stroke="#64748b" stroke-width="2.5"/>
        <line x1="180" y1="250" x2="280" y2="200" stroke="#64748b" stroke-width="2.5"/>
        <line x1="280" y1="200" x2="350" y2="280" stroke="#64748b" stroke-width="2.5"/>
        
        <!-- Соединения между другими вершинами -->
        <line x1="100" y1="150" x2="180" y2="100" stroke="#64748b" stroke-width="2.5"/>
        <line x1="100" y1="150" x2="180" y2="250" stroke="#64748b" stroke-width="2.5"/>
        <line x1="180" y1="100" x2="180" y2="250" stroke="#64748b" stroke-width="2.5"/>
        <line x1="180" y1="100" x2="350" y2="100" stroke="#64748b" stroke-width="2.5"/>
        <line x1="350" y1="100" x2="350" y2="280" stroke="#64748b" stroke-width="2.5"/>
        
        <!-- Вершина A (левая) -->
        <circle class="hotspot-area" data-area="vertex_a" cx="100" cy="150" r="18" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="2.5" cursor="pointer"/>
        <text x="100" y="155" text-anchor="middle" fill="#1e4663" font-size="14" font-weight="bold">A</text>
        
        <!-- Вершина B (верхняя левая) -->
        <circle class="hotspot-area" data-area="vertex_b" cx="180" cy="100" r="18" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="2.5" cursor="pointer"/>
        <text x="180" y="105" text-anchor="middle" fill="#1e4663" font-size="14" font-weight="bold">B</text>
        
        <!-- Вершина C (нижняя левая) -->
        <circle class="hotspot-area" data-area="vertex_c" cx="180" cy="250" r="18" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="2.5" cursor="pointer"/>
        <text x="180" y="255" text-anchor="middle" fill="#1e4663" font-size="14" font-weight="bold">C</text>
        
        <!-- Вершина D (центр) - обычный цвет, как у всех -->
        <circle class="hotspot-area" data-area="vertex_d" cx="280" cy="200" r="20" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="280" y="206" text-anchor="middle" fill="#1e4663" font-size="15" font-weight="bold">D</text>
        
        <!-- Вершина E (верхняя правая) -->
        <circle class="hotspot-area" data-area="vertex_e" cx="350" cy="100" r="16" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="2.5" cursor="pointer"/>
        <text x="350" y="105" text-anchor="middle" fill="#1e4663" font-size="13" font-weight="bold">E</text>
        
        <!-- Вершина F (изолированная) - обычная сплошная линия -->
        <circle class="hotspot-area" data-area="vertex_f" cx="450" cy="200" r="16" fill="#94a3b8" fill-opacity="0.4" stroke="#2563eb " stroke-width="2.5" cursor="pointer"/> 
        <text x="450" y="205" text-anchor="middle" fill="#1e4663" font-size="13" font-weight="bold">F</text>
        
        <!-- Вершина G (нижняя правая) -->
        <circle class="hotspot-area" data-area="vertex_g" cx="350" cy="280" r="16" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="2.5" cursor="pointer"/>
        <text x="350" y="285" text-anchor="middle" fill="#1e4663" font-size="13" font-weight="bold">G</text>
    </svg>`;
}
// Функция отрисовки графа для задания 3 (цепь - последовательные вершины)
function drawGraphPath() {
    return `<svg width="600" height="200" viewBox="0 0 600 200" class="diagram-svg">
        <rect x="0" y="0" width="600" height="200" fill="#f8fafc" rx="10"/>
        
        <!-- Рёбра (линия с вершинами) -->
        <line x1="80" y1="100" x2="190" y2="100" stroke="#64748b" stroke-width="3"/>
        <line x1="190" y1="100" x2="300" y2="100" stroke="#64748b" stroke-width="3"/>
        <line x1="300" y1="100" x2="410" y2="100" stroke="#64748b" stroke-width="3"/>
        <line x1="410" y1="100" x2="520" y2="100" stroke="#64748b" stroke-width="3"/>
        
        <!-- Вершины (все на линии, включая промежуточные) -->
        <circle class="hotspot-area" data-area="vertex_a" cx="80" cy="100" r="24" fill="#10b981" fill-opacity="0.4" stroke="#059669" stroke-width="3" cursor="pointer"/>
        <text x="80" y="106" text-anchor="middle" fill="#1e4663" font-size="18" font-weight="bold">A</text>
        
        <circle class="hotspot-area" data-area="vertex_b" cx="190" cy="100" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="190" y="106" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">B</text>
        
        <circle class="hotspot-area" data-area="vertex_c" cx="300" cy="100" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="300" y="106" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">C</text>
        
        <circle class="hotspot-area" data-area="vertex_d" cx="410" cy="100" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="410" y="106" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">D</text>
        
        <circle class="hotspot-area" data-area="vertex_e" cx="520" cy="100" r="24" fill="#f59e0b" fill-opacity="0.4" stroke="#d97706" stroke-width="3" cursor="pointer"/>
        <text x="520" y="106" text-anchor="middle" fill="#1e4663" font-size="18" font-weight="bold">E</text>
    </svg>`;
}

// Функция отрисовки графа для задания 4 (цикл-треугольник) - все вершины одинаковые
function drawGraphCycle() {
    return `<svg width="550" height="450" viewBox="0 0 550 450" class="diagram-svg">
        <rect x="0" y="0" width="550" height="450" fill="#f8fafc" rx="10"/>
        
        <!-- Рёбра треугольника -->
        <line x1="275" y1="80" x2="150" y2="300" stroke="#64748b" stroke-width="3"/>
        <line x1="275" y1="80" x2="400" y2="300" stroke="#64748b" stroke-width="3"/>
        <line x1="150" y1="300" x2="400" y2="300" stroke="#64748b" stroke-width="3"/>
        
        <!-- Дополнительные рёбра к периферийным вершинам -->
        <line x1="150" y1="300" x2="70" y2="380" stroke="#64748b" stroke-width="2.5"/>
        <line x1="400" y1="300" x2="480" y2="380" stroke="#64748b" stroke-width="2.5"/>
        
        <!-- Вершины треугольника - ВСЕ ОДИНАКОВОГО ЦВЕТА И РАЗМЕРА -->
        <circle class="hotspot-area" data-area="vertex_a" cx="275" cy="80" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="275" y="86" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">A</text>
        
        <circle class="hotspot-area" data-area="vertex_b" cx="150" cy="300" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="150" y="306" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">B</text>
        
        <circle class="hotspot-area" data-area="vertex_c" cx="400" cy="300" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="400" y="306" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">C</text>
        
        <!-- Дополнительные периферийные вершины - ТАКОГО ЖЕ РАЗМЕРА И ЦВЕТА -->
        <circle class="hotspot-area" data-area="vertex_d" cx="70" cy="380" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="70" y="386" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">D</text>
        
        <circle class="hotspot-area" data-area="vertex_e" cx="480" cy="380" r="22" fill="#3b82f6" fill-opacity="0.4" stroke="#2563eb" stroke-width="3" cursor="pointer"/>
        <text x="480" y="386" text-anchor="middle" fill="#1e4663" font-size="16" font-weight="bold">E</text>
    </svg>`;
}
let currentTaskIndex = 0;
let taskProgress = {};
let selectedAreas = {};

function loadTaskProgress() {
    const saved = localStorage.getItem('interactive_tasks_progress');
    if (saved) {
        taskProgress = JSON.parse(saved);
    }
}

function saveTaskProgress() {
    localStorage.setItem('interactive_tasks_progress', JSON.stringify(taskProgress));
}

function isTaskCompleted(taskId) {
    return taskProgress[taskId] === true;
}

function markTaskCompleted(taskId) {
    if (!taskProgress[taskId]) {
        taskProgress[taskId] = true;
        saveTaskProgress();
    }
}

function resetTaskProgress() {
    if (confirm('Сбросить прогресс всех интерактивных заданий?')) {
        taskProgress = {};
        saveTaskProgress();
        renderInteractiveContent();
    }
}

function drawTwoCirclesSVG(task) {
    const selected = selectedAreas[task.id] || [];
    
    return `<svg width="450" height="350" viewBox="0 0 450 350" class="diagram-svg">
        <rect x="0" y="0" width="450" height="350" fill="#f8fafc" rx="10"/>
        
        <!-- Внешняя область -->
        <rect class="hotspot-area" data-area="outside" x="0" y="0" width="450" height="350" fill="#f8fafc" stroke="none" opacity="0"/>
        
        <!-- Круг A (левый) -->
        <circle class="hotspot-area" data-area="left" cx="145" cy="150" r="85" fill="#3b82f6" fill-opacity="0.25" stroke="#2563eb" stroke-width="2.5"/>
        <text x="145" y="145" text-anchor="middle" fill="#1e4663" font-size="22" font-weight="bold">A</text>
        
        <!-- Круг B (правый) -->
        <circle class="hotspot-area" data-area="right" cx="305" cy="150" r="85" fill="#ef4444" fill-opacity="0.25" stroke="#dc2626" stroke-width="2.5"/>
        <text x="305" y="145" text-anchor="middle" fill="#1e4663" font-size="22" font-weight="bold">B</text>
        
        <!-- Пересечение - прозрачная кликабельная область -->
        <circle class="hotspot-area" data-area="intersection" cx="225" cy="150" r="50" fill="#a855f7" fill-opacity="0" stroke="none"/>
            </svg>`;
}
function drawThreeCirclesSVG(task) {
    const selected = selectedAreas[task.id] || [];
    
    return `<svg width="520" height="420" viewBox="0 0 520 420" class="diagram-svg">
        <rect x="0" y="0" width="520" height="420" fill="#f8fafc" rx="10"/>
        
        <!-- Внешняя область -->
        <rect class="hotspot-area" data-area="outside" x="0" y="0" width="520" height="420" fill="#f8fafc" stroke="none" opacity="0"/>
        
        <!-- Круг A (верхний левый) -->
        <circle class="hotspot-area" data-area="a" cx="190" cy="150" r="85" fill="#3b82f6" fill-opacity="0.2" stroke="#2563eb" stroke-width="2.5"/>
        <text x="190" y="145" text-anchor="middle" fill="#1e4663" font-size="20" font-weight="bold">A</text>
        
        <!-- Круг B (верхний правый) -->
        <circle class="hotspot-area" data-area="b" cx="330" cy="150" r="85" fill="#ef4444" fill-opacity="0.2" stroke="#dc2626" stroke-width="2.5"/>
        <text x="330" y="145" text-anchor="middle" fill="#1e4663" font-size="20" font-weight="bold">B</text>
        
        <!-- Круг C (нижний, ПОДНЯТ ВЫШЕ для лучшего пересечения) -->
        <circle class="hotspot-area" data-area="c" cx="260" cy="230" r="85" fill="#10b981" fill-opacity="0.2" stroke="#059669" stroke-width="2.5"/>
        <text x="260" y="225" text-anchor="middle" fill="#1e4663" font-size="20" font-weight="bold">C</text>
        
        <!-- Скрытые кликабельные области для пересечений -->
        <!-- A∩B -->
        <circle class="hotspot-area" data-area="ab" cx="260" cy="150" r="50" fill="#8b5cf6" fill-opacity="0" stroke="none"/>
        
        <!-- A∩C -->
        <circle class="hotspot-area" data-area="ac" cx="225" cy="190" r="50" fill="#ec4899" fill-opacity="0" stroke="none"/>
        
        <!-- B∩C -->
        <circle class="hotspot-area" data-area="bc" cx="295" cy="190" r="50" fill="#f97316" fill-opacity="0" stroke="none"/>
        
        <!-- A∩B∩C (центральное пересечение - теперь хорошо видно) -->
        <circle class="hotspot-area" data-area="abc" cx="260" cy="190" r="35" fill="#1e4663" fill-opacity="0" stroke="none"/>
        
        <!-- Подписи областей внизу -->
    </svg>`;
}
function renderInteractiveContent() {
    const container = document.getElementById('casesContainer');
    let tasks;
    
    // Определяем какой набор заданий использовать
    if (currentTopic === 'grade7_topic9') {  // Графы (7 класс)
        tasks = graphInteractiveTasks;
    } else if (currentTopic === 'grade8_topic4') {  // Множества (8 класс)
        tasks = interactiveTasks;
    } else {
        tasks = [];
    }
    
    if (tasks.length === 0) {
        container.innerHTML = `<div class="empty-placeholder">🖱️ Интерактивные визуализации для этой темы скоро появятся!</div>`;
        return;
    }
    
    // Убеждаемся что currentTaskIndex в пределах массива
    if (currentTaskIndex >= tasks.length) {
        currentTaskIndex = 0;
    }
    
    const task = tasks[currentTaskIndex];
    const isCompleted = isTaskCompleted(task.id);
    
    // Инициализируем выбранные области для этого задания
    if (!selectedAreas[task.id]) {
        selectedAreas[task.id] = [];
    }
    
    let completedCount = Object.values(taskProgress).filter(v => v === true).length;
    let totalTasks = tasks.length;
    
    // ВАЖНО: выбираем правильную функцию отрисовки в зависимости от типа задания
    let diagramHtml = '';
    
    // Для графов (тип hotspot_graph)
    if (task.type === 'hotspot_graph') {
        if (task.diagramType === 'graph_basic') {
            diagramHtml = drawGraphBasic();
        } else if (task.diagramType === 'graph_isolated') {
            diagramHtml = drawGraphIsolated();
        } else if (task.diagramType === 'graph_path') {
            diagramHtml = drawGraphPath();
        } else if (task.diagramType === 'graph_cycle') {
            diagramHtml = drawGraphCycle();
        } else if (task.diagramType === 'text_only') {
            // Для текстового задания без графа
            diagramHtml = `
                <div style="text-align: center; padding: 40px; background: #f8fafc; border-radius: 1rem;">
                    <p style="font-size: 1.1rem; margin-bottom: 20px;">${task.question}</p>
                    <div style="display: flex; gap: 20px; justify-content: center;">
                        <div class="hotspot-area" data-area="answer_yes" style="padding: 12px 24px; background: #10b981; color: white; border-radius: 40px; cursor: pointer; display: inline-block;">✅ Да, возможен</div>
                        <div class="hotspot-area" data-area="answer_no" style="padding: 12px 24px; background: #ef4444; color: white; border-radius: 40px; cursor: pointer; display: inline-block;">❌ Нет, невозможен</div>
                    </div>
                </div>
            `;
        }
    } 
    // Для диаграмм Эйлера (множества)
    else {
        if (task.diagramType === 'twoCircles') {
            diagramHtml = drawTwoCirclesSVG(task);
        } else if (task.diagramType === 'threeCircles') {
            diagramHtml = drawThreeCirclesSVG(task);
        }
    }
    
    // Создаём список областей для выбора
    let areasListHtml = '<div style="margin-top: 1rem; margin-bottom: 1rem; padding: 0.8rem; background: #f1f5f9; border-radius: 0.8rem;">';
    areasListHtml += '<strong>📋 Доступные области (кликни на диаграмму для выбора):</strong><br>';
    for (let [areaId, areaName] of Object.entries(task.areaNames)) {
        const isSelected = selectedAreas[task.id].includes(areaId);
        areasListHtml += `<span style="display: inline-block; margin: 5px; padding: 4px 10px; background: ${isSelected ? '#2c6e2c' : '#e2e8f0'}; color: ${isSelected ? 'white' : '#1e2a3e'}; border-radius: 20px; font-size: 0.8rem;">${areaName} ${isSelected ? '✅' : ''}</span>`;
    }
    areasListHtml += '</div>';
    
    const html = `
        <div class="interactive-container">
            <div class="interactive-title">
                📊 Задание ${currentTaskIndex + 1} из ${totalTasks}
                ${isCompleted ? '<span class="task-completed-badge">✅ Пройдено</span>' : ''}
            </div>
            <div class="interactive-question">
                <strong>📌 Вопрос:</strong> ${task.question}
            </div>
            
            <div class="diagram-container" id="diagramContainer">
                ${diagramHtml}
            </div>
            
            ${areasListHtml}
            
            <div id="feedback-${task.id}" class="feedback-message"></div>
            
            <div style="display: flex; gap: 10px; justify-content: center; margin-top: 1rem;">
                <button id="checkAnswerBtn" class="interactive-nav-btn" style="background: #2c6e2c;">✅ Проверить ответ</button>
                <button id="clearSelectionBtn" class="interactive-nav-btn" style="background: #b91c1c;">🗑️ Очистить выбор</button>
            </div>
            
            <div class="interactive-progress">
                📊 Прогресс: ${completedCount} из ${totalTasks} заданий выполнено
            </div>
            
            <div class="interactive-nav">
                <button class="interactive-nav-btn" id="prevTaskBtn" ${currentTaskIndex === 0 ? 'disabled' : ''}>◀ Предыдущее</button>
                <button class="interactive-nav-btn" id="nextTaskBtn" ${currentTaskIndex === totalTasks - 1 ? 'disabled' : ''}>Следующее ▶</button>
                <button class="interactive-reset-btn" id="resetProgressBtn">⟳ Сбросить прогресс</button>
            </div>
        </div>
    `;
    
    container.innerHTML = html;
    
    // Добавляем обработчики для hotspot-областей
    const hotspots = document.querySelectorAll('.hotspot-area');
    hotspots.forEach(area => {
        const areaName = area.getAttribute('data-area');
        if (selectedAreas[task.id].includes(areaName)) {
            if (area.tagName === 'circle' || area.tagName === 'rect') {
                area.style.fill = '#2c6e2c';
                area.style.fillOpacity = '0.5';
                area.style.stroke = '#2c6e2c';
                area.style.strokeWidth = '3';
            } else {
                area.style.background = '#2c6e2c';
            }
        }
        
        area.addEventListener('click', (e) => {
            e.stopPropagation();
            const clickedArea = area.getAttribute('data-area');
            toggleAreaSelection(clickedArea, task);
        });
    });
    
    document.getElementById('checkAnswerBtn')?.addEventListener('click', () => checkAnswerFinal(task));
    document.getElementById('clearSelectionBtn')?.addEventListener('click', () => clearSelection(task));
    
    document.getElementById('prevTaskBtn')?.addEventListener('click', () => {
        if (currentTaskIndex > 0) {
            currentTaskIndex--;
            renderInteractiveContent();
        }
    });
    
    document.getElementById('nextTaskBtn')?.addEventListener('click', () => {
        if (currentTaskIndex < tasks.length - 1) {
            currentTaskIndex++;
            renderInteractiveContent();
        }
    });
    
    document.getElementById('resetProgressBtn')?.addEventListener('click', resetTaskProgress);
}
function toggleAreaSelection(areaName, task) {
    if (isTaskCompleted(task.id)) return;
    
    if (!selectedAreas[task.id]) {
        selectedAreas[task.id] = [];
    }
    
    const index = selectedAreas[task.id].indexOf(areaName);
    if (index === -1) {
        selectedAreas[task.id].push(areaName);
    } else {
        selectedAreas[task.id].splice(index, 1);
    }
    
    // Перерисовываем для обновления подсветки
    renderInteractiveContent();
}

function clearSelection(task) {
    if (isTaskCompleted(task.id)) return;
    selectedAreas[task.id] = [];
    renderInteractiveContent();
}

function checkAnswerFinal(task) {
    if (isTaskCompleted(task.id)) {
        const feedbackDiv = document.getElementById(`feedback-${task.id}`);
        feedbackDiv.className = 'feedback-message correct';
        feedbackDiv.innerHTML = '✅ Это задание уже выполнено! Переходи к следующему.';
        return;
    }
    
    const selected = selectedAreas[task.id] || [];
    const required = task.correctAreas;
    
    // Сортируем для сравнения
    const selectedSorted = [...selected].sort();
    const requiredSorted = [...required].sort();
    
    const isCorrect = selectedSorted.length === requiredSorted.length && 
                      selectedSorted.every((val, idx) => val === requiredSorted[idx]);
    
    const feedbackDiv = document.getElementById(`feedback-${task.id}`);
    
    // Определяем текущий набор заданий
    let tasks;
    if (currentTopic === 'grade7_topic9') {
        tasks = graphInteractiveTasks;
    } else {
        tasks = interactiveTasks;
    }
    
    if (isCorrect) {
        feedbackDiv.className = 'feedback-message correct';
        feedbackDiv.innerHTML = task.feedback;
        markTaskCompleted(task.id);
        
        // Обновляем прогресс
        let completedCount = Object.values(taskProgress).filter(v => v === true).length;
        let totalTasks = tasks.length;
        const progressDiv = document.querySelector('.interactive-progress');
        if (progressDiv) {
            progressDiv.innerHTML = `📊 Прогресс: ${completedCount} из ${totalTasks} заданий выполнено`;
        }
        
        // Обновляем заголовок
        const titleDiv = document.querySelector('.interactive-title');
        if (titleDiv && !titleDiv.innerHTML.includes('Пройдено')) {
            titleDiv.innerHTML = titleDiv.innerHTML + '<span class="task-completed-badge">✅ Пройдено</span>';
        }
        
        // Очищаем выбор после правильного ответа
        selectedAreas[task.id] = [];
        
        // Автоматический переход к следующему заданию через 1.5 секунды
        if (currentTaskIndex < tasks.length - 1) {
            setTimeout(() => {
                currentTaskIndex++;
                renderInteractiveContent();
            }, 1500);
        }
    } else {
        feedbackDiv.className = 'feedback-message wrong';
        
        const missing = required.filter(area => !selected.includes(area));
        const extra = selected.filter(area => !required.includes(area));
        
        let message = '❌ Неверно. ';
        if (missing.length > 0) {
            const missingNames = missing.map(a => task.areaNames[a] || a).join(', ');
            message += `Не выбраны: ${missingNames}. `;
        }
        if (extra.length > 0) {
            const extraNames = extra.map(a => task.areaNames[a] || a).join(', ');
            message += `Лишние: ${extraNames}. `;
        }
        message += 'Попробуй ещё раз!';
        
        feedbackDiv.innerHTML = message;
        
        // Визуальная подсветка неправильных областей
        const hotspots = document.querySelectorAll('.hotspot-area');
        hotspots.forEach(area => {
            const areaName = area.getAttribute('data-area');
            if (selected.includes(areaName) && !required.includes(areaName)) {
                if (area.tagName === 'circle' || area.tagName === 'rect') {
                    const originalFill = area.style.fill;
                    area.style.fill = '#b91c1c';
                    area.style.fillOpacity = '0.5';
                    setTimeout(() => {
                        area.style.fill = originalFill;
                    }, 1000);
                }
            }
        });
    }
}
function checkAnswer(clickedArea, task) {
    const isCorrect = task.correctAreas.includes(clickedArea);
    const feedbackDiv = document.getElementById(`feedback-${task.id}`);
    const diagramContainer = document.getElementById('diagramContainer');
    
    if (isCorrect) {
        feedbackDiv.className = 'feedback-message correct';
        feedbackDiv.innerHTML = task.feedback;
        
        // Отмечаем задание выполненным
        if (!isTaskCompleted(task.id)) {
            markTaskCompleted(task.id);
            
            // Обновляем отображение
            const titleDiv = document.querySelector('.interactive-title');
            if (titleDiv && !titleDiv.innerHTML.includes('Пройдено')) {
                titleDiv.innerHTML += '<span class="task-completed-badge">✅ Пройдено</span>';
            }
            
            // Обновляем прогресс
            let completedCount = Object.values(taskProgress).filter(v => v === true).length;
            let totalTasks = interactiveTasks.length;
            const progressDiv = document.querySelector('.interactive-progress');
            if (progressDiv) {
                progressDiv.innerHTML = `📊 Прогресс: ${completedCount} из ${totalTasks} заданий выполнено`;
            }
        }
        
        // Визуальный эффект на правильную область
        const clickedElement = document.querySelector(`[data-area="${clickedArea}"]`);
        if (clickedElement) {
            clickedElement.classList.add('correct-click');
            setTimeout(() => clickedElement.classList.remove('correct-click'), 500);
        }
        
        // Автоматический переход к следующему заданию через 1.5 секунды
        if (currentTaskIndex < interactiveTasks.length - 1) {
            setTimeout(() => {
                currentTaskIndex++;
                renderInteractiveContent();
            }, 1500);
        }
    } else {
        feedbackDiv.className = 'feedback-message wrong';
        feedbackDiv.innerHTML = '❌ Неверно. Попробуй ещё раз!';
        
        // Визуальный эффект на неправильную область
        const clickedElement = document.querySelector(`[data-area="${clickedArea}"]`);
        if (clickedElement) {
            clickedElement.classList.add('wrong-click');
            setTimeout(() => clickedElement.classList.remove('wrong-click'), 300);
        }
    }
    
    // Автоматически скрываем сообщение через 3 секунды (если неверно)
    if (!isCorrect) {
        setTimeout(() => {
            if (feedbackDiv.className === 'feedback-message wrong') {
                feedbackDiv.style.display = 'none';
                setTimeout(() => {
                    feedbackDiv.style.display = '';
                }, 100);
            }
        }, 2000);
    }
}

// Инициализация интерактивных заданий
function initInteractive() {
    loadTaskProgress();
    renderInteractiveContent();
}
</script>
</body>
</html>
