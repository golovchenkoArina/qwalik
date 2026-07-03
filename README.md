<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Чек-лист для преподавателя</title>
    <style>
        /* ---- Общие стили ---- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #f0f4f8;
            padding: 40px 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .container {
            max-width: 1100px;
            width: 100%;
            background: #ffffff;
            border-radius: 24px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.08);
            padding: 40px 45px;
            margin-bottom: 30px;
        }
        h1 {
            font-size: 28px;
            font-weight: 600;
            color: #0b1e33;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .subhead {
            color: #5a6e85;
            font-size: 16px;
            border-left: 4px solid #3b82f6;
            padding-left: 16px;
            margin-top: -2px;
            margin-bottom: 30px;
        }
        h2 {
            font-size: 20px;
            font-weight: 600;
            color: #0b1e33;
            margin-top: 36px;
            margin-bottom: 16px;
            padding-bottom: 8px;
            border-bottom: 2px solid #e9edf2;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .badge {
            background: #3b82f6;
            color: white;
            font-size: 13px;
            font-weight: 500;
            padding: 2px 14px;
            border-radius: 30px;
            letter-spacing: 0.3px;
        }
        .badge-green {
            background: #22a65e;
        }

        /* ---- Карточки шагов ---- */
        .steps-grid {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        .step {
            display: flex;
            align-items: flex-start;
            gap: 14px;
            padding: 14px 18px;
            border-radius: 12px;
            background: #f8faff;
            border: 1px solid #e9edf2;
            transition: background 0.15s;
        }
        .step:hover {
            background: #f2f7ff;
        }
        .step-num {
            font-weight: 600;
            color: #3b82f6;
            background: #e1ebff;
            border-radius: 30px;
            padding: 2px 12px;
            font-size: 14px;
            white-space: nowrap;
            margin-top: 1px;
        }
        .step-content {
            flex: 1;
            line-height: 1.5;
        }
        .step-content strong {
            color: #0b1e33;
        }
        .cmd {
            display: inline-block;
            background: #1e2a3a;
            color: #e2e8f0;
            font-family: 'Fira Code', 'Courier New', monospace;
            font-size: 14px;
            padding: 4px 14px;
            border-radius: 8px;
            margin-top: 4px;
            word-break: break-all;
        }
        .result {
            color: #1f7b4a;
            font-weight: 500;
            margin-left: 6px;
        }
        .result::before {
            content: "✅ ";
        }

        /* ---- Таблица бэкапов (чек-лист) ---- */
        .backup-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 15px;
            border-radius: 14px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.02);
        }
        .backup-table th {
            background: #f0f4fc;
            color: #1a2b3e;
            font-weight: 600;
            text-align: left;
            padding: 14px 18px;
            border-bottom: 2px solid #dce2eb;
        }
        .backup-table td {
            padding: 14px 18px;
            border-bottom: 1px solid #e9edf2;
            vertical-align: top;
            line-height: 1.5;
        }
        .backup-table tr:last-child td {
            border-bottom: none;
        }
        .backup-table .cmd-cell {
            font-family: 'Fira Code', 'Courier New', monospace;
            font-size: 14px;
            background: #f7f9fc;
            border-radius: 6px;
            padding: 6px 12px;
            display: inline-block;
            word-break: break-all;
        }
        .backup-table .status {
            color: #1f7b4a;
            font-weight: 500;
            white-space: nowrap;
        }
        .backup-table .status::before {
            content: "✅ ";
        }

        /* ---- Адаптив ---- */
        @media (max-width: 700px) {
            .container {
                padding: 22px 18px;
            }
            h1 {
                font-size: 22px;
                flex-wrap: wrap;
            }
            .step {
                flex-wrap: wrap;
                padding: 12px 14px;
            }
            .backup-table th,
            .backup-table td {
                padding: 12px 14px;
                font-size: 14px;
            }
            .backup-table .cmd-cell {
                font-size: 13px;
                word-break: break-all;
                white-space: normal;
            }
        }
        @media print {
            body {
                background: white;
                padding: 20px;
            }
            .container {
                box-shadow: none;
                border: 1px solid #ddd;
            }
            .step:hover {
                background: #f8faff;
            }
        }

        /* ---- Иконки/эмодзи как в задании ---- */
        .emoji-icon {
            font-size: 20px;
            line-height: 1;
        }
        .section-icon {
            font-size: 22px;
            margin-right: 6px;
        }
    </style>
</head>
<body>

    <!-- ============================================================ -->
    <!--  БЛОК 1: УСТАНОВКА ПО / ЭКЗАМЕН                          -->
    <!-- ============================================================ -->
    <div class="container">
        <h1>
            <span class="emoji-icon">⚙️</span> Чек-лист установки
        </h1>
        <div class="subhead">
            Группа 301ИС-23 · Подготовка рабочей среды
        </div>

        <div class="steps-grid">
            <!-- 1 -->
            <div class="step">
                <span class="step-num">1</span>
                <div class="step-content">
                    <strong>Установка базового ПО</strong>
                    <div><span class="cmd">sudo apt update</span></div>
                    <div><span class="cmd">sudo apt upgrade -y</span></div>
                </div>
            </div>
            <!-- 2 -->
            <div class="step">
                <span class="step-num">2</span>
                <div class="step-content">
                    <strong>Установка драйверов</strong>
                    <div><span class="cmd">sudo ubuntu-drivers autoinstall</span></div>
                </div>
            </div>
            <!-- 3 -->
            <div class="step">
                <span class="step-num">3</span>
                <div class="step-content">
                    <strong>Базовый набор утилит</strong>
                    <div><span class="cmd">sudo apt install -y curl wget git net-tools htop nano vim mc tree</span></div>
                </div>
            </div>
            <!-- 4 -->
            <div class="step">
                <span class="step-num">4</span>
                <div class="step-content">
                    <strong>Архиватор</strong>
                    <div><span class="cmd">sudo apt install -y p7zip-full p7zip-rar</span></div>
                </div>
            </div>
            <!-- 5 -->
            <div class="step">
                <span class="step-num">5</span>
                <div class="step-content">
                    <strong>Графический редактор GIMP</strong>
                    <div><span class="cmd">sudo apt install -y gimp</span></div>
                </div>
            </div>
            <!-- 6 -->
            <div class="step">
                <span class="step-num">6</span>
                <div class="step-content">
                    <strong>Офисный пакет LibreOffice</strong>
                    <div><span class="cmd">sudo apt install -y libreoffice libreoffice-l10n-ru</span></div>
                </div>
            </div>
            <!-- 7 -->
            <div class="step">
                <span class="step-num">7</span>
                <div class="step-content">
                    <strong>Антивирус ClamAV</strong>
                    <div><span class="cmd">sudo apt install -y clamav clamav-daemon</span></div>
                </div>
            </div>
            <!-- 8 -->
            <div class="step">
                <span class="step-num">8</span>
                <div class="step-content">
                    <strong>Среда разработки (VS Code)</strong>
                    <div><span class="cmd">sudo snap install --classic code</span></div>
                </div>
            </div>
            <!-- 9 -->
            <div class="step">
                <span class="step-num">9</span>
                <div class="step-content">
                    <strong>Виртуальный принтер (PDF)</strong>
                    <div><span class="cmd">sudo apt update</span></div>
                    <div><span class="cmd">sudo apt install cups-pdf</span></div>
                </div>
            </div>
            <!-- 10 -->
            <div class="step">
                <span class="step-num">10</span>
                <div class="step-content">
                    <strong>Директория для PDF</strong>
                    <div><span class="cmd">mkdir -p ~/PDF</span></div>
                </div>
            </div>
            <!-- 11 -->
            <div class="step">
                <span class="step-num">11</span>
                <div class="step-content">
                    <strong>Тест печати (виртуальный принтер)</strong>
                    <div><span class="cmd">echo "Тест печати. Группа 301ИС-23" &gt; test.txt</span></div>
                    <div><span class="cmd">lp -d PDF test.txt</span></div>
                </div>
            </div>
            <!-- 12 -->
            <div class="step">
                <span class="step-num">12</span>
                <div class="step-content">
                    <strong>Точка восстановления (Timeshift)</strong>
                    <div><span class="cmd">sudo apt install -y timeshift</span></div>
                    <div><span class="cmd">sudo timeshift --create --comments "Экзамен ПМ.04 - точка восстановления"</span></div>
                    <div><span class="cmd">sudo timeshift --list</span></div>
                </div>
            </div>
            <!-- 13 -->
            <div class="step">
                <span class="step-num">13</span>
                <div class="step-content">
                    <strong>Группа и пользователи</strong>
                    <div><span class="cmd">sudo groupadd students</span></div>
                    <div><span class="cmd">sudo adduser student1</span></div>
                    <div><span class="cmd">sudo usermod -aG students student1</span></div>
                </div>
            </div>
            <!-- 14 -->
            <div class="step">
                <span class="step-num">14</span>
                <div class="step-content">
                    <strong>Настройка прав доступа</strong>
                    <div><span class="cmd">mkdir test</span></div>
                    <div><span class="cmd">sudo chown student1:students test</span></div>
                    <div><span class="cmd">chmod 770 test</span></div>
                </div>
            </div>
            <!-- 15 -->
            <div class="step">
                <span class="step-num">15</span>
                <div class="step-content">
                    <strong>Аутентификация и журналирование</strong>
                    <div><span class="cmd">journalctl</span></div>
                    <div><span class="cmd">journalctl -n 20</span></div>
                    <div><span class="cmd">last</span></div>
                </div>
            </div>
            <!-- 16 -->
            <div class="step">
                <span class="step-num">16</span>
                <div class="step-content">
                    <strong>Проверка совместимости</strong>
                    <div><span class="cmd">apt-cache depends gimp</span></div>
                    <div><span class="cmd">gimp --version</span></div>
                </div>
            </div>
        </div>

        <p style="margin-top: 28px; color: #5a6e85; font-size: 14px; border-top: 1px solid #e9edf2; padding-top: 20px;">
            ✅ Все шаги выполнены успешно.
        </p>
    </div>

    <!-- ============================================================ -->
    <!--  БЛОК 2: БЭКАПЫ (ИТОГОВЫЙ ЧЕК-ЛИСТ ДЛЯ ПРЕПОДАВАТЕЛЯ)        -->
    <!-- ============================================================ -->
    <div class="container">
        <h1>
            <span class="emoji-icon">💾</span> Итоговый чек-лист для преподавателя
        </h1>
        <div class="subhead">
            Резервное копирование &bull; Проверка &bull; Восстановление
        </div>

        <table class="backup-table">
            <thead>
                <tr>
                    <th style="width:28%;">Действие</th>
                    <th style="width:52%;">Команда</th>
                    <th style="width:20%;">Результат</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td><strong>Создание папки для бэкапов</strong></td>
                    <td><span class="cmd-cell">sudo mkdir -p /backup</span></td>
                    <td><span class="status">Папка создана</span></td>
                </tr>
                <tr>
                    <td><strong>Бэкап системы (tar)</strong></td>
                    <td><span class="cmd-cell">sudo tar -czpf /backup/backup.tar.gz --exclude=/proc --exclude=/sys --exclude=/dev --exclude=/tmp /</span></td>
                    <td><span class="status">Архив создан</span></td>
                </tr>
                <tr>
                    <td><strong>Бэкап через rsync</strong></td>
                    <td><span class="cmd-cell">sudo rsync -aAXv --exclude={/proc,/sys,/dev,/tmp} / /backup/system/</span></td>
                    <td><span class="status">Копия создана</span></td>
                </tr>
                <tr>
                    <td><strong>Точка восстановления (Timeshift)</strong></td>
                    <td><span class="cmd-cell">sudo timeshift --create --comments "Точка"</span></td>
                    <td><span class="status">Точка создана</span></td>
                </tr>
                <tr>
                    <td><strong>Проверка бэкапов</strong></td>
                    <td><span class="cmd-cell">ls -lh /backup/</span></td>
                    <td><span class="status">Все файлы видны</span></td>
                </tr>
                <tr>
                    <td><strong>Размер бэкапа</strong></td>
                    <td><span class="cmd-cell">du -sh /backup/*</span></td>
                    <td><span class="status">Размер отображается</span></td>
                </tr>
            </tbody>
        </table>

        <p style="margin-top: 24px; color: #5a6e85; font-size: 14px;">
            ✅ Все пункты выполнены — система готова.
        </p>
    </div>

</body>
</html>
