# Chapter 12: Cutting through attributes, properties, and CSS
* Cases where `property` names and `attribute` names differ
      Attribute name => Property name
      for => htmlFor
      class => className
      readonly => readOnly
      maxlength => maxLength
      cellspacing => cellSpacing
      rowspan => rowSpan
      colspan => colSpan
      tabindex =>tabIndex
      cellpadding => cellPadding
      usemap => useMap
      frameborder => frameBorder
      contenteditable => contentEditable
* In general, `property` access is faster than the corresponding DOM `attribute` methods
* when accessing a `property` that references a URL (such as `href`, `src`, or `action`) the URL value is automatically converted from its original form into a full canonical URL.
* The `offsetHeight` and `offsetWidth` properties provide a fairly reliable means to access the actual `height` and `width` of an element. But be aware that the values assigned to these two properties include the `padding` of the element.
* Obtain non-hidden dimensions for hidden elements (`display: none`):
  1. Change the `display` property to `block`.
  2. Set `visibility` to `hidden`.
  3. Set `position` to `absolute`.
  4. Grab the dimension values.
  5. Restore the changed properties.
* CSS3 color formats:
  - keyword: Any of the recognized HTML color keywords (`red`, `green`, `maroon`, and so on), extended SVG color keywords (`bisque`, `chocolate`, `darkred`, and so on), or the keyword `transparent` (which is equivalent to `rgba(0,0,0,0)`—see below).
  - `#rgb`: Short hexadecimal RGB (`red`, `green`, `blue`) color values, where each portion is a value from 0 to f.
  - `#rrggbb`: Long hexadecimal RGB (`red`, `green`, `blue`) color values, where each portion is a value from 00 to ff.
  - `rgb(r, g, b)`: RGB notation where each value is a decimal value from 0 to 255, or 0% to 100%.
  - `rgba(r, g, b, a)`: RGB notation with the addition of an alpha channel. The alpha value ranges from 0.0 (transparent) to 1.0 (fully opaque).
  - `hsl(h, s, l)`: HSL notation where the values represent hue, saturation, and lightness. The hue value ranges from 0 to 360 (the angle on the color wheel), and saturation and lightness range from 0% to 100%.
  - `hsla(h, s, l, a)`: HSL notation with the addition of the alpha channel.
