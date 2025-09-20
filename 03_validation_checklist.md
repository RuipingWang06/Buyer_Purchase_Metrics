### ✅ Visual Design & Functionality Checklist

- **Filtering**
  - Apply filter conditions to exclude elements with blank or zero values.
  - Ensure "Select All" option is available for filter dropdowns.

- **Chart Elements**
  - Titles, Y-axis labels, and legends should be clearly named and meaningful.

- **Bookmark & Filter Interactivity**
  - Bookmarks should retain and reflect the correct filter states.
  - Filters should interact properly with visuals.

- **Visual Interactions**
  - Ensure correct interactions between filters and visuals.
  - Ensure expected cross-filtering behavior among visuals.

- **Keep All Filter Buttons Enabled**
  - It’s recommended to turn **“Keep All Filters”** **ON** when setting up drillthrough.
  - This ensures that filters applied on the **source page** will automatically pass to the **target page**, as long as both pages are using the **same dataset/table**.
  - However, if the source and target pages **use different datasets or tables**, there’s **no need to enable** this option, since the data will be filtered based on:
    - The defined **relationships**, and
    - The selected **drillthrough field(s)**.

- **Zero Value Handling**
  - Related dimension values should still be displayed even when the metric value is 0.
 
