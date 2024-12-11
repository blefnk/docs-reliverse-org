---
title: Principles, Design Decisions, Code Insights, Recommendations
description: This is the principles, design decisions, code insights, and recommendations of Relivator.
---

> "У володінні ~~Porsche~~ Relivator є багато непрактичних речей. Але всі вони компенсуються враженнями від водіння. Він справді унікальний. Ламборджині ~~Lamborghini~~ create-t3-app та Феррарі ~~Ferrari~~ Vercel Store наближаються до нього. І вони більш потужні в певних випадках, але вони не керуються так, як ~~Porsche~~ Relivator". © ~~Кевін О'Лірі~~ [@blefnk](https://github.com/blefnk)

*Ми постійно вдосконалюємо цей розділ. Будь ласка, вносьте свої пропозиції!

Наш стартап має на меті стати багатим ресурсом для розробників на всіх етапах їхньої подорожі. У блоках коментарів та спеціальних розділах в кінці окремих файлів ви знайдете цінні поради та роз'яснення з широкого спектру тем. Внесок у покращення цих освітніх самородків дуже заохочується!

**Принципи (W.I.P.):**

- [x] Принцип Преттера щодо досвіду розробника ([джерело](https://prettier.io/docs/en/integrating-with-linters.html#notes)): "У результаті ви отримуєте багато червоних хвилястих ліній у редакторі, які починають дратувати. Prettier повинен змусити вас забути про форматування - а не показувати його в обличчя!"
- [x] Кожен файл і компонент слід створювати свідомо, використовуючи [принципи KISS/DRY/SOLID/YAGNI](https://blog.openreplay.com/applying-design-principles-in-react) з певним почуттям інтелекту і з думкою про продуктивність.
- [x] Ми повинні думати про проект, як про планету зі своїми континентами, країнами, містами, кімнатами, особами, організаціями і т.д.

Розширені змінні оточення:** *Розширені змінні оточення:**

Файл `.env.example` містить всі основні змінні для повнофункціонального веб-сайту, призначеного для початківців. Однак, якщо вам потрібні розширені конфігурації, ви можете змінити будь-яке значення у файлі `.env` за потреби.

Про папку плагінів:** *Про папку плагінів:**

Ця тека містить додаткові плагіни для Relivator. Розроблені @blefnk та іншими учасниками, ці плагіни розширюють функціональність і надають додаткові можливості. Якщо ви вважаєте, що певні плагіни не є корисними для проекту, не соромтеся видаляти відповідні теки.

**Функція над константою для компонентів:**

Ми рекомендуємо використовувати ключове слово `function` замість `const` при визначенні React-компонентів. Використання `function` часто покращує трасування стеку, що полегшує налагодження. Крім того, це робить семантику коду більш явною, тим самим полегшуючи іншим розробникам розуміння намірів.

**Особисті рекомендації:**

Ми рекомендуємо регулярно очищати кеш браузера і видаляти папку `.next` для забезпечення оптимальної продуктивності і функціональності.

Наразі ми не використовуємо Contentlayer через його нестабільну роботу з Windows. Тому ми вивчаємо можливості його використання в конфігураційному файлі `.env`. В майбутньому ми плануємо розробити власне рішення для написання контенту. Інтеграція із зовнішніми провайдерами, такими як Sanity, також може стати майбутньою функцією, з відповідними опціями ввімкнення/вимкнення.

ПРИМІТКА зі сторінки [Contentlayer Issues Page](https://github.com/contentlayerdev/contentlayer/issues/313#issuecomment-1305424923): Contentlayer погано працює з `next.config.mjs`, тому вам потрібно мати `next.config.js`. Інші бібліотеки також можуть вимагати цього. Якщо ви впевнені, що вам потрібен `.mjs` і не плануєте використовувати Contentlayer, перейменуйте його.

**Конфігурація проекту:**

У файлі `rc/app.ts` містяться основні конфігурації для зміни вмісту та налаштувань веб-сайту, що дозволяє вам

- Керувати вмістом, представленим на веб-сайті.
- Налаштовувати різні параметри, наприклад, деактивувати перемикач тем.
- Керувати загальною інформацією на сайті.

Налаштувати цей файл відповідно до вимог.

**Автентифікація:**

Налаштування автентифікації дуже просте.

Ви можете налаштувати доступні для Clerk провайдери входу в систему у файлі `src/app.ts`.

Будь ласка, пам'ятайте, що Clerk повноцінно працює зі сторонніми сервісами, такими як "Google PageSpeed Insight", лише за умови використання доменних і живих ключів.

*Цей розділ буде реалізовано найближчим часом.

Конфігурація скриптів: **Тип скриптів:**

У файлі `tsconfig.json` ви можете встановити параметри для компілятора TypeScript. Ви можете навести курсор на кожну опцію, щоб отримати додаткову інформацію. Підказка: Ви також можете натиснути Shift+пробіл, щоб отримати автозавершення. Щоб дізнатися більше, зверніться до офіційної документації TypeScript: @дивіться <https://typescriptlang.org/docs/handbook/tsconfig-json> @дивіться <https://totaltypescript.com/tsconfig-cheat-sheet>.

Next.js має вбудовану підтримку TypeScript за допомогою плагіна нижче. Але якщо ви використовуєте `bun run build`, він зупиняється на першій же помилці типу. Тому ви можете використовувати `bun typecheck` для перевірки всіх попереджень/помилок одразу.

Конфіг включає плагін Atomic CSS в атрибуті style. Статичні стилі з підтримкою тем, адаптивних варіантів і без інтеграції з бандлерами, безпечні за типом. @див. <https://github.com/tokenami/tokenami#readme>.

Ви можете увімкнути сувору перевірку типів у MDX-файлах, встановивши `mdx.checkMdx` у true.

Ці параметри, наведені нижче, може бути небезпечно встановлювати у значення false, коли ви поступово переходите до повної безпеки типів.

```json
{
  "alwaysStrict": true,
  "noImplicitAny": false,
  "strict": true,
  "strictNullChecks": true,
  "strictPropertyInitialization": true,
  "verbatimModuleSyntax": true
}
```

**Як розгорнути проект:**

Будь ласка, ознайомтеся з розділом *Як встановити та розпочати роботу* перед початком розгортання.

Зверніться до посібників з розгортання для [Vercel](https://create.t3.gg/en/deployment/vercel), [Netlify](https://create.t3.gg/en/deployment/netlify) та [Docker](https://create.t3.gg/en/deployment/docker) для отримання більш детальної інформації. Проект було протестовано лише на Vercel; будь ласка, повідомте нас, якщо у вас виникнуть проблеми з іншими сервісами розгортання.

**Стилістика, система дизайну, компоненти інтерфейсу користувача:**

TODO: Реалізувати систему дизайну та керівництво по стилю.

За замовчуванням цей проект включає компоненти з різних бібліотек, а також нестилізовані [shadcn/ui](https://ui.shadcn.com) компоненти. Shadcn/ui навіть дозволяє генерувати нові компоненти інтерфейсу користувача за допомогою свого CLI (де "кнопкою" може бути будь-який елемент інтерфейсу користувача Shadcn): `bunx shadcn-ui@latest add button`.

W.I.P. - Використовуйте `bun css` для відстеження [токенів CSS](https://blog.devgenius.io/link-figma-and-react-using-figma-tokens-89e6cc874b4d) відповідно до системи дизайну проекту. Очікується, що для цієї концепції будуть використані [Tokenami](https://github.com/tokenami/tokenami#readme) та Figma. Для отримання додаткової інформації зверніться до пунктів #33 та #90 дорожньої карти Relivator.

**Сумісність з менеджером пакунків:**

У `Relivator` вже можна використовувати деякі фантастичні можливості **[`bun`](<https://bun> .sh)**. Для початку ми рекомендуємо використовувати `pnpm`. Повну підтримку та сумісність bun буде надано, щойно [Reliverse](https://github.com/blefnk/reliverse) досягне повної подібності до [Relivator](https://github.com/blefnk/relivator) у [Relivator](https://github.com/blefnk/relivator). *Розширення розділу незабаром.*

**Рекомендовані речі для вивчення:**

1. [Детальний посібник з Git'у](https://github.com/blefnk/relivator/blob/main/.github/GITGUIDE.md) від [Назара Корнієнка @Blefnk](https://github.com/blefnk)
2. [Вступ до Next.js та React](https://youtube.com/watch?v=h2BcitZPMn4) від [Lee Robinson](https://x.com/leeerob)
3. [Relivator: Next.js 15 Starter (Анонс релізу Relivator на Medium)](https://cutt.ly/awf6fScS) від [Назар Корнієнко @Blefnk](https://github.com/blefnk)
4. [Ласкаво просимо у дикий світ TypeScript, друже! Це страшно?](https://cutt.ly/CwjVPUNu) від [Назар Корнієнко @Blefnk](https://github.com/blefnk)
5. [React: типові помилки у 2023 році](https://docs.google.com/presentation/d/1kuBeSh-yTrL031IlmuwrZ8LvavOGzSbo) від [Cory House](https://x.com/housecor)
6. [Думки про Next.js 13, Server Actions, Drizzle, Neon, Clerk та інше](https://github.com/Apestein/nextflix/blob/main/README.md#overall-thoughts) від [@Apestein](https://github.com/Apestein)
7. [Величезна багатомовна довідка про i18n](https://github.com/Avansai/next-multilingual#readme) від [@Avansai](https://github.com/Avansai)
8. [Застосування принципів дизайну в React](https://blog.openreplay.com/applying-design-principles-in-react) від [Jeremiah (Jerry) Ezekwu](https://blog.openreplay.com/authors/jeremiah-\(jerry\)-ezekwu/)
9. [The Power of Prototyping Code](https://medium.com/@joomiguelcunha/the-power-of-prototyping-code-55f4ed485a30) від [João Miguel Cunha](https://medium.com/@joomiguelcunha)
10. [Прототипування програмного забезпечення](https://en.wikipedia.org/wiki/Software_prototyping) у Вікіпедії
11. [TDD: Test-driven development](https://en.wikipedia.org/wiki/Test-driven_development) у Вікіпедії
12. [React 19 RC Announcement](https://react.dev/blog/2024/04/25/react-19) на [React](https://react.dev)

*Більше навчальних ресурсів можна знайти у файлах цього репозиторію.