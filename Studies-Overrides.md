One may override default inputs values or style (color, line thickness e.t.c) of every indicator with `studies_overrides` parameter. `studies_overrides` is expected to be an object where key is a path to property being changed and value is the new value for it. Example:
```
studies_overrides: {
    "volume.volume.color.0": "#00FFFF",
    "volume.volume.color.1": "#0000FF",
    "volume.volume.transparency": 70,
    "volume.volume ma.color": "#FF0000",
    "volume.volume ma.transparency": 30,
    "volume.volume ma.linewidth": 5,
    "volume.show ma": true,
    "volume.options.showStudyArguments": false,
    "bollinger bands.median.color": "#33FF88",
    "bollinger bands.upper.linewidth": 7
}
```

#Syntax

Property path is a set of lower-case identifiers splitted with dot (`.`). Path formats are described below.

###Study input
Format: `indicator_name.input_name`

* **indicator_name**: use name as you can see it in `Indicators` dialog.  
* **input_name**: use name as you can see it in indicator's properties dialog (see figure 1 below) -- i.e., `show ma`

Examples: `volume.show ma`, `bollinger bands.length`

###Plot property
Format: `indicator_name.plot_name.property_name`

* **indicator_name**:  < ... >
* **plot_name**: as you can see it in indicator's properties dialog (see figure 2 below) -- i.e., `Volume`
* **property_name**: one of the following:
  * **transparency**
  * **linewidth**
  * **plottype**. Supported plot types are:
    * line
    * histogram
    * cross
    * area
    * columns
    * circles
    * line_with_breaks
    * area_with_breaks


Examples: `volume.volume.transparency`, `bollinger bands.median.linewidth`

###Plot colors
Format: `indicator_name.plot_name.color<.color_index>`

* **indicator_name**:  < ... >
* **plot_name**:  < ... >
* **color**. It is just a keyword.
* **color_index** (optional): color index (if any). It's just an ordinal number of a color for this plot. I.e., to replace the color which is green by default for Volume, one should use `color_index = 1`.

**Remark 1**: `color.0` is a synonym of `color` .So paths `volume.volume.color.0` and `volume.volume.color` are treated to be the same.

**Remark 2**: For now, customizing area fill color and transparency is not supported.

**Limitations**:
* Only `#RRGGBB` format is supported for colors. Do not use short format `#RGB`.
* Transparency varies in [0..100] range. 100 means plot is fully opaque.
* Thickness is an integer.

###Study options
Format: `indicator_name.options.option_name`

* **indicator_name**:  < ... >
* **options**:  Keyword
* **option_name**: name of option you want to assign. Supported values are:
  * **showStudyArguments**: boolean, controls arguments visibility in header
  * **showLastValue**: boolean, controls visibility of price scale labels

Examples: `volume.options.showStudyArguments`, `volume.options.showLastValue`