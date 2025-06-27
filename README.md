# Air Web

A demo visualization built with Astro and Air.

⚠️⚠️⚠️ The project is not complete. I'm a junior/mid frontend dev at best, so I wasn't able to finish the data visualization. The rest is basically ok. ⚠️⚠️⚠️

I left the generate code for the potential data visualization in the `DataPicker.astro` file, but it seems like Astro is a bad choice over react as it's either under-documented (so LLMs do not have "experience" with it yet) or has some DOM issues I cannot figure out on my own.


On the other branch, Junie was actually able to generate the visualization with this prompt chain:

```
now we need to add a second set of cards, directly after the StepCards component. these cards will have a border radius of 8px. the card on the left a #19191c background, the one on the right white. text will be white on the card on the left, black on the one on the right. same width as step cards.
-
margin top should be -1rem, as they need to be really sticking to the parent. the left card will display two selects: Programming Language and Country. data must be taken from calculatordata.json. calculatordata probably needs to be remapped as the schema of the json is a bit different. font size should be about 1.4 rem.
-
sort the programming languages and the country in alphabetical order. the select will start from the first. the card on the right will display this text: `Coding specialists from Brazil who use C / C++ reported to have the following gross annual salaries (in USD including bonuses) in 2024:` , where Brazil and c/c++ will be dynamic based on the selected things from the card on the left. these dynamic parts will have a text color of #6b57ff
-
make font size about for card-text about 2rem.  check diagnostics as i have some typescript errors
-
i still have this error: Astro: Element implicitly has an any type because expression of type string can't be used to index type
{ "United States": { "JavaScript / TypeScript": { entries: { value: number; category: string; metadata: { Country: string; Language: string; Experience: string; Salary: string; }; }[]; yGroups: string[]; xRangeGroups: number[][]; xRange: string[]; }; 
... 9 more ...; Rust: { ...; }; }; 
... 13 more ...; Italy: { ...; ...
No index signature with a parameter of type string was found on type
{ "United States": { "JavaScript / TypeScript": { entries: { value: number; category: string; metadata: { Country: string; Language: s
-
now  <select id="programming-language" name="programming-language">
          {programmingLanguages.map(language => (
            <option value={language}>{language}</option>
          ))}
        </select> here says option value language is any so Astro: Type unknown is not assignable to type string | number | string[] | null | undefine
-
now we need to add a visualization for the salary data. it MUST live into the right card; it will be a cartesian graph, with x axis being salaries (keep only some relevant, start from 0 and end to 400k) and y axis years of experiences. put dots where the entries are
-
the visualization is fantastic. hope we can do some changes: plot the legend of the y axis on the right; make the x-axis calculated dynamically based on the salaries, as sometimes it overflow as people earn more than 500k; the background of the visualization should be white; if possible join the dots on the same yoy by  a line.
-
last changes: make a small grid inside the visualization, for clarity, use a gray not a black; if possible, on hover of a dot, i'd love to see the specific data for that dot in a small hover window
```

I was very impressed as it got first time, while air made a scatter plot in a totally different div.

## Run the project:

Clone the repo and:

`npm install && npm run dev` or `npm install && npm run build && npm run preview`
