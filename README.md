# Build My Plate

A kid-friendly meal picker that makes building a balanced plate easy, with a simple log so parents can see what was eaten.

Kids pick foods for breakfast, lunch, and dinner. Each food has color bars showing its main macros. "Sometimes foods" (chips, crackers, dessert) stay locked until they've picked enough growing food and a fruit or veggie.

It's a single HTML file with no dependencies, no build step, and no server.

## How it works

- **Three meals:** Breakfast, Lunch, and Dinner tabs, each with its own plate.
- **Three food groups:**
  - **Growing food:** protein, dairy, grains, and snacks that build a meal
  - **Fruits + veggies:** their own section
  - **Sometimes foods:** chips, crackers, and desserts
- **Unlock rules:** Sometimes foods unlock after **2 growing foods** and **1 fruit or veggie**. Up to **2 sometimes foods** per meal.
- **Macro colors:** red is protein, yellow is carbs + fiber, blue is fat, and purple is a sometimes food. Foods with more than one macro show more than one bar.
- **My plate panel:** shows the picks so far and which macros are covered. It's a sticky side panel on iPad and desktop, and a bottom bar on phones.
- **Parent log:** when a meal is saved it goes into the Log tab. You can copy the day as text, remove a single meal, or clear the whole day. "Clear today" is also at the top of every page.

## Run it

Open `index.html` in a browser. That's it.

To host it:

- **GitHub Pages:** Settings, then Pages, then deploy from the `main` branch root. Your site will be at `https://<username>.github.io/<repo>/`.
- **Home network:** put the file on any static web server and open it from other devices by its address.

Keep using the same address on a given device, because the saved log is tied to it.

## Add to an iPad Home Screen

1. Open the page in Safari.
2. Tap Share, then **Add to Home Screen**.
3. Open it from the new icon, and use that icon from then on.

The Home Screen icon and Safari keep their own separate storage, so pick one way to open it and stick with it.

## Customize

Everything lives in `index.html`. Foods are in the `ITEMS` list near the top of the script:

```js
// name, emoji, macros, type
["Chicken stick","🍗","p","g"],
["Apples","🍏","c","v"],
["Goldfish","🐟","cf","d"],
```

- **Macros:** `p` is protein, `c` is carbs + fiber, `f` is fat. Combine letters, like `"pc"` for protein and carbs.
- **Type:** `g` is growing food, `v` is fruit or veggie, and `d` is a sometimes food.
- **Unlock rules** are set by one line:

  ```js
  var NEED=2,NEEDV=1,MAXD=2;
  ```

  `NEED` is the number of growing foods required, `NEEDV` is the number of fruits or veggies required, and `MAXD` is the most sometimes foods per meal.

To try a new food, add a line to `ITEMS`. To retire one, delete its line.

## Data and privacy

Nothing leaves the device. The day's log is stored in the browser's local storage on whatever device the kid uses, resets each day, and isn't synced anywhere. Use **Copy as text** in the Log tab to send a day's meals to your phone.

## Version

The current version is shown in the page footer (for example `kid-menu-v5`).
