---
title: "Introducing My Date Difference Calculator"
date: 2025-03-09 12:00:00 -0500
categories: [blog, Projects, JavaScript]
tags: [web-development, tools, calculator]
---

# Introducing My Date Difference Calculator

I’ve been working on a small but handy tool recently: a **Date Difference Calculator**. It’s a simple web-based utility that calculates the number of days between two dates, with an option to include the end date in the count. I built it using HTML, CSS, and JavaScript, and I’m excited to share it with you!

You can try it out live here: [Date Difference Calculator](https://jasonbra1n.github.io/date-calculator/). The source code is available on GitHub: [jasonbra1n/date-calculator](https://github.com/jasonbra1n/date-calculator). Below, I’ve embedded it directly into this post so you can test it right here!

## Try It Out

Here’s the calculator in action:

<iframe src="https://jasonbra1n.github.io/date-calculator/" width="400" height="400" frameborder="0" style="display: block; margin: 0 auto;"></iframe>

Pick a start date, an end date, and check the "Include End Date" box if you want that extra day counted. Hit "Calculate" to see the result!

## What It Does

The Date Difference Calculator is straightforward:
- Pick a **Start Date** and an **End Date** using the built-in date pickers.
- Check the "Include End Date" box if you want the end date counted as an extra day.
- Hit the "Calculate" button, and it’ll tell you the number of days between the two dates.

For example, if you select March 1st to March 5th:
- Without including the end date, it returns **4 days**.
- With the end date included, it returns **5 days**.

It’s a clean, no-frills tool that I’ve found useful for quick date math—whether for project planning, tracking deadlines, or just satisfying curiosity.

## What’s New

I’ve improved the calculator to be more flexible:
- **Responsive Design**: It scales to 90% of its container’s width (up to 400px), so it fits iframes without horizontal scrollbars.
- **Height Adjustment**: The layout adapts to its content, reducing vertical scrollbars unless necessary.
- **Mobile-Friendly**: Smaller screens get adjusted padding and font sizes.

## How It Works

The calculator is a single HTML file with embedded CSS and JavaScript. Here’s a quick breakdown:

- **HTML**: A simple form with two date inputs, a checkbox, a button, and a result div.
- **CSS**: A styled container with a light background, subtle shadows, and responsive inputs. It’s designed to look polished but not overdone.
- **JavaScript**: The core logic grabs the dates, calculates the time difference in milliseconds, converts it to days, and adjusts based on the "Include End Date" option. It also handles invalid inputs gracefully.

Here’s a snippet of the JavaScript that does the heavy lifting:

```javascript
function calculateDifference() {
    const startDate = new Date(document.getElementById('startDate').value);
    const endDate = new Date(document.getElementById('endDate').value);
    const includeEndDate = document.getElementById('includeEndDate').checked;

    if (isNaN(startDate) || isNaN(endDate)) {
        document.getElementById('result').innerText = "Please enter valid dates.";
        return;
    }

    const diffInTime = endDate - startDate;
    const diffInDays = Math.ceil(diffInTime / (1000 * 60 * 60 * 24));
    const result = includeEndDate ? diffInDays + 1 : diffInDays;

    document.getElementById('result').innerText = `The difference is ${result} day(s).`;
}
