# Homework 2 — Graduate Critical Thinking Evidence

**Student:** Monica Sai Chalasani  
**Browser used for all evidence:** ____________________  
**Live URL / local path visible in screenshots:** ____________________

> Important: The assignment requires evidence from your own submitted page.
> Do not invent measurements. Record them from the browser DevTools Computed
> and Layout panels.

## Question 03 — Architecture Defense

### Screenshot A — exactly 700px viewport
Save as: `evidence/q3-700px.png`

Record:
- Viewport width: 700px
- Computed `.content-frame` width: __________
- Computed `.review-region` width: __________
- Computed `.overview` width: __________
- Horizontal overflow observed: Yes / No

### Screenshot B — exactly 480px viewport
Save as: `evidence/q3-480px.png`

Record:
- Viewport width: 480px
- Computed `.content-frame` width: __________
- Computed `.review-region` width: __________
- Computed `.overview` width: __________
- Horizontal overflow observed: Yes / No

### Related Grid excerpt

```css
.content-frame {
    display: grid;
    grid-template-areas:
        "reviews overview"
        "counter counter";
    grid-template-columns: minmax(0, 1fr) 250px;
}

@media (max-width: 700px) {
    .content-frame {
        grid-template-areas:
            "reviews"
            "overview"
            "counter";
        grid-template-columns: minmax(0, 1fr);
    }
}
```

### Related Flexbox excerpt

```css
.reviewer {
    display: flex;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 5px;
}
```

### Your defense
Use your actual measurements above.

Grid is appropriate for the large page regions because it controls the
two-dimensional relationship between the reviews, overview panel, and counter.
At the 700px breakpoint, the named areas change from two columns to a stacked
one-column structure.

Flexbox is appropriate for each reviewer row because the critic icon and text
form a one-dimensional repeated component. `flex-wrap: wrap` lets the metadata
adapt if the available width becomes narrow.

Add your measured evidence here:
________________________________________________________________________
________________________________________________________________________
________________________________________________________________________


## Question 04 — Failure Analysis

Make a **separate copy** of the page. Do not damage the final `index.html`.

Suggested controlled defect:
1. Copy `styles.css` to `evidence/broken-styles.css`.
2. In that copy, temporarily change this mobile rule:

```css
.reviews-grid {
    grid-template-columns: minmax(0, 1fr);
}
```

to:

```css
.reviews-grid {
    grid-template-columns: 550px 550px;
}
```

3. Link the broken copy only while collecting evidence.
4. Set the viewport to 480px.
5. Capture the visible horizontal overflow/clipping.
6. Restore the correct stylesheet before submission.

### Defect screenshot
Save as: `evidence/q4-defect.png`

### Diagnosis
Record:
- Viewport width: __________
- Scroll width from DevTools: __________
- Visible symptom: ______________________________________________
- Root cause: a fixed two-column width is wider than the mobile content area,
  so the grid cannot shrink and causes horizontal overflow.

### Corrected screenshot
Save as: `evidence/q4-corrected.png`

### Corrected rule

```css
@media (max-width: 480px) {
    .reviews-grid {
        grid-template-columns: minmax(0, 1fr);
    }
}
```

### Your final explanation
________________________________________________________________________
________________________________________________________________________
________________________________________________________________________


## Accessibility / focus audit

Test with the Tab key and record:
- Official movie site receives visible focus: Yes / No
- HTML validator link receives visible focus: Yes / No
- CSS validator link receives visible focus: Yes / No
- Focus is clearly visible: Yes / No

CSS used:

```css
a:focus-visible {
    outline: 3px solid #000;
    outline-offset: 2px;
}
```


## Print layout evidence

Open Print Preview and confirm:
- Banner is hidden: Yes / No
- Fixed validator controls are hidden: Yes / No
- Reviews do not clip: Yes / No
- Overview remains readable: Yes / No
