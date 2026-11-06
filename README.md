# Veggie Recipe Finder

A single-page website that searches several recipe sources at once for vegetarian recipes matching a keyword such as `Italian`, `pizza` or `dessert`. It is one static file (`index.html`) with no build step and no dependencies.

## Run it

Open `index.html` in a browser. You need an internet connection because the recipes come from online APIs.

## Features

- One search box queries every source and merges the results.
- Quick-search buttons and cuisine/category chips for browsing.
- Click a card to see ingredients, instructions and a link to the original recipe or video.
- Each card shows which source it came from.
- Light and dark theme, following the system setting.
- After each search, link buttons open the same search on other recipe sites (Cookie and Kate, Minimalist Baker, Budget Bytes and others). These only link out; nothing is copied from those sites.

## Sources

| Source | How it is used | Vegetarian filtering |
| --- | --- | --- |
| [TheMealDB](https://www.themealdb.com/api.php) | Preloaded on page load, searched locally | Keyword filter |
| [DummyJSON](https://dummyjson.com/docs/recipes) | Preloaded on page load, searched locally | Keyword filter |
| [Spoonacular](https://spoonacular.com/food-api) | Live search on every query | `diet=vegetarian` |
| [Wikibooks Cookbook](https://en.wikibooks.org/wiki/Cookbook:Table_of_Contents) | Live search on every query | Only pages tagged vegetarian or vegan |
| [API Ninjas](https://api-ninjas.com/api/recipe) | Live search on every query | Keyword filter |

The keyword filter (the `MEAT` regular expression in `index.html`) drops any recipe whose title or ingredients mention meat or fish, and TheMealDB's beef, chicken, lamb, pork, seafood and goat categories. It is a best guess, so check the ingredients of anything borderline.

## API keys

The Spoonacular and API Ninjas keys are set as constants near the top of the script in `index.html` (`SPOON_KEY`, and `ninjaKey`). Replace them with your own if you fork this project.

The keys are visible to anyone who can open the page. Do not reuse keys that are tied to billing or that you want to keep private.

## Deploy

The project is a static site. `render.yaml` describes a free static site for [Render](https://render.com):

1. Push this folder to a GitHub repository.
2. In Render, choose **New → Blueprint** and select the repository.

Any other static host (GitHub Pages, Netlify, Cloudflare Pages) also works by serving `index.html`.

## Notes and limits

- The free plans of Spoonacular and API Ninjas have daily or per-search limits. If a source stops returning results, you have probably hit its quota.
- Some recipes have no photo, so those cards show a placeholder.
- Recipes belong to their original sources. Check each source's terms before using them commercially.
