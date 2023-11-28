# TailwindCss

## Create a Tailwind config file

Run **npx tailwindcss init** in the root of your project to create a tailwind config file

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./build/*.html', './build/js/*.js'],
  theme: {
    extend: {
 
    },
  },
  plugins: [],
}
```

## Package json

Run **npm init -y** in the root of your project to create a package.json file

package.json

```json
{
  "name": "lesson2",
  "version": "1.0.0",
  "description": "",
  "main": "tailwind.config.js",
  "scripts": {
    "tailwind": "npx tailwindcss -i ./src/input.css -o ./build/css/style.css --watch",
    "prettier": "npx prettier --write **/*.html"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "prettier-plugin-tailwindcss": "^0.5.7"
  }
}
```	
add a **.gitignore** file to the root of the project directory to ignore the **node_modules** folder

```javascript	
    node_modules
```

Run **npm run tailwind** to run tailwind in watch mode




## Tailwind VSCode Extensions

| Extension                                  | Description                                                                                    |
|--------------------------------------------|------------------------------------------------------------------------------------------------|
| `Inline Fold - Mohammed Alamri`            | A custom decorator that "fold" matching content in single line                                 |
| `Tailwind CSS Intellisense - Tailwind Labs`| Intelligent Tailwind CSS tooling for VS Code                                                   |





### How to get rid off the underlined Unknown errors in tailwind

Go to File -> Preferences -> Settings 
Search for **Unknown** and select **ignore** in CSS>Lint:Unknown At Rules

### How get Tailwind Intellisense when using Emmet

Go to  Settings of **Tailwind CSS Intellisense** 
and enable **Tailwind CSS > Emmet Completions**
