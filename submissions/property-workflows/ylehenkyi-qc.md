# Здача WS6

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: ylehenkyi-qc
- Ваше репо: https://github.com/ylehenkyi-qc/property-workflows
- SHA: 56b509e244e47b5a0a6dbdd60d1b7e3bb5845911
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://pmwp-ylehenkyi.vercel.app/

## PM

—

## Розробник

- Рядок «Вимоги:» з `docs/conformance.md` на SHA: Вимоги: https://github.com/solomchaak/property-workflows-spec · джерело: issues · знімок 2026-10-19
- Перший PR «Оновлення вимог»: https://github.com/ylehenkyi-qc/property-workflows/pull/2
- Журнал `docs/spec-reading.md`: https://github.com/ylehenkyi-qc/property-workflows/blob/56b509e244e47b5a0a6dbdd60d1b7e3bb5845911/docs/spec-reading.md
- Питання в репо PM (щонайменше 3, з них щонайменше 1 — власне issue): https://github.com/solomchaak/property-workflows-spec/issues/6, https://github.com/solomchaak/property-workflows-spec/issues/7, https://github.com/solomchaak/property-workflows-spec/issues/4#issuecomment-6273815465
- PR «Специфікація» з перекладом першого зрізу: https://github.com/ylehenkyi-qc/property-workflows/pull/3
- Зміна `impl-run-tasks`: https://github.com/ylehenkyi-qc/property-workflows/tree/56b509e244e47b5a0a6dbdd60d1b7e3bb5845911/openspec/changes/archive/2026-10-20-impl-run-tasks
- PR-и задач «Реалізація» (щонайменше 2): https://github.com/ylehenkyi-qc/property-workflows/pull/6, https://github.com/ylehenkyi-qc/property-workflows/pull/7, https://github.com/ylehenkyi-qc/property-workflows/pull/8
- PR «Оновлення вимог» після уточнень PM: https://github.com/ylehenkyi-qc/property-workflows/pull/2 — /requirements-sync 2026-10-20: Вимоги актуальні
- PR «Специфікація» зі змінами після уточнень: змін у вимогах PM не було
- AC, які ви реалізували: AC-RUN-03 (реалізовано), AC-RUN-07 (реалізовано), AC-TASK-05 (реалізовано), AC-TASK-08 (реалізовано), AC-TASK-09 (реалізовано); решта відкладено (DB-тести не запускаються в CI) — як у docs/conformance.md на SHA

## Бонус E

Розробник: `/opsx:verify impl-run-tasks` + розбір знахідок: https://gist.github.com/ylehenkyi-qc/06e4882ede36be1c26b34cc0fede224c

Verify знайшов розбіжність між галочками в tasks.md і реально виконаним (немає DB-тестів), а також 13 із 18 AC з правилами в Postgres поза автоперевіркою, чого не ловлять npm test і ac:coverage. Помилився він у двох WARNING (ручна перевірка й db-check): не бачить CI та ручного прогону.