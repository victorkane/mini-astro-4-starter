# Module 3. Markdown and MDX

## Create Astro instance

```text
victor@victorpc:M03-markdown-and-mdx$ pwd
/home/victor/Work/Learn/Astro/2023/coding-in-public/LearnAstro/dev/
victor@victorpc:dev$ npm create astro@latest M03-markdown-and-mdx
Need to install the following packages:
create-astro@4.7.0
Ok to proceed? (y) y

 astro   Launch sequence initiated.

      ◼  dir Using M03-markdown-and-mdx as project directory

  tmpl   How would you like to start your new project?
         Empty

  deps   Install dependencies?
         Yes

    ts   Do you plan to write TypeScript?
         Yes

   use   How strict should TypeScript be?
         Strict

   git   Initialize a new git repository?
         Yes

      ✔  Project initialized!
         ■ Template copied
         ■ Dependencies installed
         ■ TypeScript customized
         ■ Git initialized

  next   Liftoff confirmed. Explore your project!

         Enter your project directory using cd ./M03-markdown-and-mdx
         Run npm run dev to start the dev server. CTRL+C to stop.
         Add frameworks like react or tailwind using astro add.

         Stuck? Join us at https://astro.build/chat

╭──🎄─╮  Houston:
│ ◠ ◡ ◠  Good luck out there, astronaut! 🚀
╰─────╯

victor@victorpc:dev$ cd M03-markdown-and-mdx/
victor@victorpc:M03-markdown-and-mdx$ pwd
/home/victor/Work/Learn/Astro/2023/coding-in-public/LearnAstro/dev/M03-markdown-and-mdx
victor@victorpc:M03-markdown-and-mdx$ code .
```

- initial commit

```bash
commit f71893c1c54c34e441f42e5c743c256d9abe9a76 (HEAD -> main)
Author: victorkane <victorkane@gmail.com>
Date:   Thu Jan 4 15:02:03 2024 -0300

    Initial commit

 .gitignore              |   21 +
 .vscode/extensions.json |    4 +
 .vscode/launch.json     |   11 +
 README.md               |   47 +
 astro.config.mjs        |    4 +
 package-lock.json       | 6551 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 package.json            |   17 +
 public/favicon.svg      |    9 +
 src/env.d.ts            |    1 +
 src/pages/index.astro   |   16 +
 tsconfig.json           |    3 +
 11 files changed, 6684 insertions(+)
```

- Configure main branch after initial commit

```bash
victor@victorpc:M03-markdown-and-mdx$ git branch -M main
```

- Run local dev instance

```bash
ictor@victorpc:M03-markdown-and-mdx$ npm run dev

> m03-markdown-and-mdx@0.0.1 dev
> astro dev


 astro  v4.1.0 ready in 85 ms

┃ Local    http://localhost:4321/
┃ Network  use --host to expose

16:11:49 watching for file changes...
```

## Astro VS Code support

- Steps

  - Install [Astro VS Code plugin](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode)
  - Install Prettier and the astro plugin

    ```bash
    npm i --save-dev prettier prettier-plugin-astro
    ```

    - Add the following settings your (optionally user or workspace) settings:
      ```bash
        "editor.formatOnPaste": true,
        "editor.formatOnSave": true,
        "prettier.documentSelectors": ["**/*.astro"],
        "[astro]": {
          "editor.defaultFormatter": "esbenp.prettier-vscode"
        }
      ```
    - Sample local prettier configuration files (taken from [Astro doc theme Starlight](https://github.com/withastro/starlight))

      ```bash
      victor@victorpc:astro-course-files$ cat .prettierrc
      {
        "printWidth": 100,
        "semi": true,
        "singleQuote": true,
        "tabWidth": 2,
        "trailingComma": "es5",
        "useTabs": true,
        "plugins": ["prettier-plugin-astro"],
        "overrides": [
          {
            "files": [".*", "*.json", "*.md", "*.toml", "*.yml"],
            "options": {
              "useTabs": false
            }
          },
          {
            "files": ["*.md", "*.mdx"],
            "options": {
              "printWidth": 80
            }
          }
        ]
      }

      victor@victorpc:astro-course-files$ cat .prettierignore
      # Deep Directories
      **/node_modules

      # Generated Directories
      **/dist
      **/.astro
      **/__coverage__

      # Directories
      .changeset

      # Files
      ```

- Commit

```bash
commit 6ee193c9d562e12a66434afcfddfd7d1edb17941 (HEAD -> main)
Author: victorkane <victorkane@gmail.com>
Date:   Thu Jan 4 16:38:23 2024 -0300

    chore(editor): Configure Astro VS Code support

 .prettierignore       |  13 +++
 .prettierrc           |  23 ++++++
 .vscode/settings.json |   8 ++
 README.md             | 175 +++++++++++++++++++++++++++++++++-------
 package-lock.json     |  63 +++++++++++++++
 package.json          |   6 +-
 src/pages/index.astro |   1 +
 7 files changed, 257 insertions(+), 32 deletions(-)
```

## Add Astro Tailwind integration

```bash
victor@victorpc:M03-markdown-and-mdx$ npx astro add tailwind
✔ Resolving packages...
16:40:48
  Astro will run the following command:
  If you skip this step, you can always run it yourself later

 ╭──────────────────────────────────────────────────────────╮
 │ npm install @astrojs/tailwind@^5.1.0 tailwindcss@^3.4.0  │
 ╰──────────────────────────────────────────────────────────╯

✔ Continue? … yes
✔ Installing dependencies...
16:41:00
  Astro will generate a minimal ./tailwind.config.mjs file.

✔ Continue? … yes
16:41:14
  Astro will make the following changes to your config file:

 ╭ astro.config.mjs ─────────────────────────────╮
 │ import { defineConfig } from 'astro/config';  │
 │                                               │
 │ import tailwind from "@astrojs/tailwind";     │
 │                                               │
 │ // https://astro.build/config                 │
 │ export default defineConfig({                 │
 │   integrations: [tailwind()]                  │
 │ });                                           │
 ╰───────────────────────────────────────────────╯

✔ Continue? … yes
16:41:24
   success  Added the following integration to your project:
  - @astrojs/tailwind
```

- Commit

```bash
commit 253b52c5bcae5fc4f785298d000155edd413ffc6 (HEAD -> main)
Author: victorkane <victorkane@gmail.com>
Date:   Thu Jan 4 16:49:36 2024 -0300

    build(style): Add Astro Tailwind integration

 README.md           |  61 ++++
 astro.config.mjs    |   6 +-
 package-lock.json   | 706 ++++++++++++++++++++++++++++++++++++++++++
 package.json        |   2 +
 tailwind.config.mjs |   8 +
 5 files changed, 782 insertions(+), 1 deletion(-)
```

- Add Tailwind CSS IntelliSense extension for VS Code user/workspace

```bash
victor@victorpc:M03-markdown-and-mdx$ cat .vscode/extensions.json
{
  "recommendations": ["astro-build.astro-vscode", "bradlc.vscode-tailwindcss"],
  "unwantedRecommendations": []
}
```
