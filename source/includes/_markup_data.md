# Markup data

Field | Description
--------- | -----------
type | Always "Feature"
properties | Contains markup specific data (style, description, etc.)
geometry | Describes markup shape

<aside class="notice">
    Polygon coordinates are [x,y] in clockwise order starting with top left corner
</aside>

<aside class="notice">
    <a href="http://geojson.org/geojson-spec.html">GeoJSON spec</a>
</aside>

## Cloud
```
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "cloud",
            "arcRadius": 8
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[240,139],[1136,139],[1136,323],[240,323]
            ]
        }
    }
}
```

Property | Description
--------- | -----------
style | Always 'cloud'
color | Color of markup
arcRadius | Radius in pixels of each cloud arc

<aside class="notice">
    Polygon coordinates refer to the exact point where the arcs of the cloud should intersect
</aside>
<aside class="notice">
    Height and width of polygon must be evenly divisible by the arc radius
</aside>

## Text box

``` json
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "text",
            "description": "line 1\nline 2\nline 3",
            "fontSize": 8
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]
            ]
        }
    }
}
```

Property | Description
--------- | -----------
style | Always 'text'
color | Color of markup
description | Text to be displayed (newlines marked with '\n')
fontSize | Size of text in pixels

<aside class="notice">
    Polygon coordinates refer to the bounding box that contains the text (with 5 pixel padding from edges)
</aside>
<aside class="notice">
    Text should not display outside box, but individual lines can wrap to fit
</aside>

## Rectangle

```
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "rectangle",
            "color": "#FF0000",
            "width": 10
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[362,62],[590,62],[590,244],[362,244]]
        }
    }
}
```

Property | Description
--------- | -----------
style | Always 'rectangle'
color | Color of markup
width | Stroke width


<aside class="notice">
    Outer rectangle (always white) is drawn at coordinates with specified stroke width
</aside>
<aside class="notice">
    Inner rectangle (using color defined in properties) is drawn inside the outer rectangle by a margin of stroke width
</aside>
<aside class="notice">
    Inner rectangle has fill opacity of 0.2
</aside>

## Drawing (Pen)

```
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "drawing",
            "color": "#FF0000",
            "width": 40
        },
        "geometry": {
            "type": "LineString",
            "coordinates": [[563,374],[563,373] ...... [565,380],[563,380]]
        }
    }
}
```

Property | Description
--------- | -----------
style | Always 'drawing'
color | Color of markup
width | Stroke width

<aside class="notice">
    Outer line (always white) has specified stroke width
</aside>
<aside class="notice">
    Inner line (using color defined in properties) has stroke width / 2
</aside>

## Arrow

```
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "arrow",
            "color": "#FF0000",
            "width": 5
        },
        "geometry": {
            "type": "LineString",
            "coordinates": [[56,399],[326,272]]
        }
    }
}
```

Property | Description
--------- | -----------
style | Always 'arrow'
color | Color of markup
width | Stroke width

<aside class="notice">
    Arrow has outline (always white) with specified stroke width and fill with specified color
</aside>

Isosceles triangle:

* Arrow height = width * 12
* Arrow width =  Arrow height / 2

## Measurement

```
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "measurement",
            "color": "#FF0000",
            "width": 5,
            "description": "15'5\"",
            "fontSize": 48
        },
        "geometry": {
            "type": "LineString",
            "coordinates": [[455,168],[1085,219]
            ]
        }
    }
}
```

Property | Description
--------- | -----------
style | Always 'arrow'
color | Color of markup
width | Stroke width
description | Text to be displayed (single line)
fontSize | Size of text in pixels

<aside class="notice">
    Line connecting arrows should provide gap to fit text
</aside>
<aside class="notice">
    Do not draw arrows if text width is larger than markup width
</aside>
<aside class="notice">
    Text should rotate between -90 and 90 degrees only
</aside>


Equilateral triangle:

* Arrow height = Arrow width = width * 6