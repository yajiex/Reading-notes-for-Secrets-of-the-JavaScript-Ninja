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
