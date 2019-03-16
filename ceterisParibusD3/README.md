# ceterisParibusD3

...

## Documentation

Package has one main function `createPlot` that is evoked on global package object `ceterisParibusD3`:

```javascript
var plot = new ceterisParibusD3.createPlot(div, data, dataObs, options);
```
where

Parameter | Type | Required| Description
------------ |  -------------| -------------| -------------
`div` |  string or div element with id | yes | id of div container for a plot or div container itself (selected by call of e.g. `document.getElementById("myDiv")`)
`data` |  array of objects | yes | data with *Ceteris Paribus Profiles* curves coordinates, see details in section *Data paremeters* below
`dataObs` |  array of objects | yes | data with observations used to generate *Ceteris Paribus Profiles* , see details in section *Data paremeters* below
`options` |  object | yes | options of the chart, see details in section *Options* below

##### Data parameters

...

##### Options

Options that can be set by `options` parameter:

Option | Type | Default | Required| Description
------------ |  -------------| -------------| -------------| -------------
`variables` |  array of strings|   | **yes** | names of variables to be plotted; should be compatible with variables from `data` and `dataObs`
`show_profiles` | boolean |  |  **yes** | If true,  ICE lines are plotted
`show_observations` | boolean |  |  **yes** | If true,  observation points are plotted
`show_rugs` | boolean |  |  **yes** | If true,  rugs are plotted
`show_residuals` | boolean |  |  **yes** | If true,  residuals  are plotted
`aggregate_profiles` | string | null |  **yes** | If 'mean', PDPs are plotted (calculated as mean of ICE's), if 'median' PDPs are plotted (calculated as median of ICE's)
`width` | number | 600 | no | width of the plot, in px
`height` | number | 400 | no | height of the plot, in px
`auto_resize` | boolean | true| no | If true, plot will be resized when its container will be resized (it includes resize of subplots, legend and fonts)
`color` |  string |  '#3F547F' | no |  name of variable that should be used for coloring elements of the chart (use `_label_` to color by model type) or color name/hex code; if categorical variable is set to be a color variable, it should have max. 10 categories
`no_colors` |  number |  3 | no |  number of colors to be used for sequential palette when `color` is set as quantitative variable,  from 1 to 9
`add_table` |  boolean |  true | no | If true, table with observations from `dataObs` will be plotted below plots (taking half of the whole chart height)
`categorical_order` |  array of objects |  null | no | definition of order of categories for categorical variables, each object in the array corresponds to one categorical variable and has key `variable` which value is string with name of variable and keys called `rank1`, `rank2` etc.  (number of these keys corresponds to number of categories of this variable) which values are strings with categories, see example in section *Usage*
`size_rugs` |  number |  1 | no |  size of rugs, from 0 to 1
`size_points` |  number |  3 | no |  size of points, in px
`size_residuals` |  number |  2 | no |  size of residuals lines and points, in px
`size_pdps` |  number |  3.5 | no |  size of residuals lines and points, in px
`size_ices` |  number |  2 | no |  size of residuals lines and points, in px
`alpha_rugs` |  number |  0.9 | no |  transparency of rugs, from 0 to 1
`alpha_points` | number | 0.9   |  no |   transparency of points, from 0 to 1
`alpha_residuals` |  number |  0.9 | no |  transparency of residuals points and lines, from 0 to 1
`alpha_pdps` |  number |  0.4 | no |  transparency of PDP ines, from 0 to 1
`alpha_ices` |  number |  0.4 | no |  transparency of ICE lines, from 0 to 1
`color_rugs` |  string  |  '#3F547F'  |  no |   rugs color name/hex code 
`color_points` | string    | '#3F547F'   |  no |   points color name/hex code 
`color_residuals` | string   |  '#3F547F'  | no  |   residuals points and lines color name/hex code 
`color_pdps` |  string  | 'grey'   | no  | PDP lines color name/hex code 
`font_size_plot_title` |  number  | 16   | no  | font size of plot title, in px
`font_size_titles` |  number  | 14  | no  | font size of subplots' title, in px
`font_size_legend` |  number  | 12 | no  | font size of legend elements, in px
`font_size_axes` |  number  | 12 | no  | font size of axes elements, in px
`font_size_tootlips` |  number  | 10 | no  | font size of tooltip text, in px
`font_size_table` |  number  | 12 | no  | font size of table's text, in px
`plot_title` |  string  | 'Ceteris Paribus plots per variable - predictions vs. variable values' | no  | title of plot
`yaxis_title` |  string  | 'y' | no  | title of y axes



##### Usage

Example of code usage on exemplary data [`example12`](https://github.com/MI2DataLab/ceterisParibusExt/blob/master/ceterisParibusD3/examples/example12.js) and [`example_obs12`](https://github.com/MI2DataLab/ceterisParibusExt/blob/master/ceterisParibusD3/examples/example_obs12.js):

```javascript
var plot = new ceterisParibusD3.createPlot(div = "chartDiv", 
                       data = example12,
                       dataObs = example_obs12, 
                       options = {
                                   variables: ["district",  "floor", 'no.rooms'],
                                   color: 'district',
                                   show_profiles: true, 
                                   show_observations: true, 
                                   show_rugs: true, 
                                   show_residuals: true, 
                                   aggregate_profiles: 'mean',
                                   add_table: true,
                                   no_colors: 3,
                                   height: 400,
                                   width: 800,
                                   size_rugs: 0.5,
                                   yaxis_title: '',
                                   color_rugs: 'grey',
                                   categorical_order: [
                                   { 'variable': 'district', 
                                     'rank1': "Bielany", 
                                     'rank2': "Bemowo", 
                                     'rank3': "Mokotow", 
                                     'rank4': "Ochota", 
                                     'rank5': "Praga", 
                                     'rank6': "Srodmiescie", 
                                     'rank7': "Ursus", 
                                     'rank8': "Ursynow", 
                                     'rank9': "Wola", 
                                     'rank10': "Zoliborz"
                                  }]  
                                }
                       );
```

## Issues and suggestions

To report a bug or propose a new feature please review these guidelines:

* make sure you have the latest version of the package
* check whether it is not already in [Issues](https://github.com/MI2DataLab/ceterisParibusExt/issues)
* add an issue following suitable template: for [bugs](https://github.com/MI2DataLab/ceterisParibusExt/blob/master/ceterisParibusD3/bug_template.md) or for [suggestions](https://github.com/MI2DataLab/ceterisParibusExt/blob/master/ceterisParibusD3/suggestion_template.md)

