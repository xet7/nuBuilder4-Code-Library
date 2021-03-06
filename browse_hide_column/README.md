### Hide a Column in a Browse Screen

This code snippet shows how to hide a column in a Browse Screen. 
Possible applications are, for example, if columns should not be displayed for certain access levels or if the object is displayed in an iFrame.

The function setBrowseColumnSize(), as its name says, also allows to resize columns.

☛ In you form's Custom Code, paste this JavaScript:

```javascript
function iniFrame() {
    return window.location !== window.parent.location;
}

function setBrowseColumnSize(column, size) {
    var cw = this;
    if (iniFrame()) {
        cw = parent.$("#" + window.frameElement.id)[0].contentWindow;
    }
    cw.nuFORM.breadcrumbs[cw.nuFORM.breadcrumbs.length - 1].column_widths[column] = size;
    cw.nuSetBrowserColumns(cw.nuFORM.breadcrumbs[cw.nuFORM.breadcrumbs.length - 1].column_widths)
}

// Example, Hide the first column 
$(function () {
    setBrowseColumnSize(0, 0);
});
```
