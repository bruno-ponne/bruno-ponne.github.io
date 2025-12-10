---
title: "A/B Testing in Tableau: Safe, Native, and Statistically Rigorous"
author: "Bruno Gasparotto Ponne - bruno.ponne@gmail.com"
layout: project
abstract: "A native Tableau dashboard for A/B testing that calculates statistical significance and required sample size without external scripts. This tool helps businesses make data-driven decisions by avoiding common pitfalls like 'peeking' and ensures reliable results through rigorous statistical methods."
image: ab_test_dashboard.png
---

### Introduction

A/B testing is the gold standard for making data-driven decisions in product development and marketing. However, a common pitfall in the business world is **"peeking"**—checking results too early and stopping a test as soon as it looks significant. This leads to false positives and decisions based on noise rather than signal.

To address this, I developed a **Tableau Public Dashboard** that not only tracks the performance of control vs. treatment groups but also rigorously calculates **Statistical Significance** and **Minimum Sample Size** natively within Tableau.

<br>

<div class='tableauPlaceholder' id='viz1733940000000' style='position: relative'>
    <noscript>
        <a href='#'><img alt='Dashboard 1 ' src='https://public.tableau.com/static/images/Cl/Click-throughRateABTest/ABTestDashboard/1_rss.png' style='border: none' /></a>
    </noscript>
    <object class='tableauViz'  style='display:none;'>
        <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
        <param name='embed_code_version' value='3' />
        <param name='site_root' value='' />
        <param name='name' value='Click-throughRateABTest/ABTestDashboard' />
        <param name='tabs' value='no' />
        <param name='toolbar' value='yes' />
        <param name='static_image' value='https://public.tableau.com/static/images/Cl/Click-throughRateABTest/ABTestDashboard/1.png' />
        <param name='animate_transition' value='yes' />
        <param name='display_static_image' value='yes' />
        <param name='display_spinner' value='yes' />
        <param name='display_overlay' value='yes' />
        <param name='display_count' value='yes' />
        <param name='language' value='en-US' />
    </object>
</div>
<script type='text/javascript'>
    var divElement = document.getElementById('viz1733940000000');
    var vizElement = divElement.getElementsByTagName('object')[0];
    // Changed fixed 1000px width to 100% to fill the container
    if ( divElement.offsetWidth > 800 ) { vizElement.style.width='100%';vizElement.style.height='827px';} else if ( divElement.offsetWidth > 500 ) { vizElement.style.width='100%';vizElement.style.height='827px';} else { vizElement.style.width='100%';vizElement.style.height='1127px';}
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>

<br>

### Methodology

Unlike many Tableau solutions that rely on external R or Python scripts, this dashboard performs all statistical calculations using native Tableau Calculated Fields. This ensures the dashboard is fast, portable, and easy to maintain.

#### 1. Sample Size Calculation
Before analyzing the results, it is crucial to determine how much data is needed. If you stop a test before reaching this threshold, your results may not be reliable. I implemented the sample size formula for **two independent proportions** based on the methodology from [Select Statistical Consultants](https://select-statistics.co.uk/calculators/sample-size-calculator-two-proportions/).

The formula requires:
* **Significance Level:** Typically 5% (95% confidence).
* **Power:** Typically 80%.
* **Baseline Conversion Rate:** The current performance of the control group.
* **Minimum Detectable Effect (MDE):** The smallest improvement you want to be able to detect.

The dashboard dynamically calculates the required n (sample size per group) to ensure the test has enough power to detect the MDE.

#### 2. Statistical Significance (Z-Test)
To determine if the difference between the Control (A) and Treatment (B) groups is real, I employed a **Z-test for Two Independent Proportions**. 

Following the statistical framework from [Penn State University](https://online.stat.psu.edu/stat200/book/export/html/193), the dashboard calculates:
* **Pooled Proportion**: A weighted average of the proportions from both groups.
* **Standard Error:** Calculated using the pooled proportion.
* **Z-Score:** The number of standard deviations the result is from the null hypothesis (no difference).

If the Z-Score exceeds the critical value (e.g., 1.96 for 95% confidence) the dashboard flags the result as statistically significant.

### Advantages Over Other Approaches

While resources like [Playfair Data's Guide](https://playfairdata.com/tableau/how-to-analyze-a-b-tests-in-tableau-using-z-tests/) offer excellent introductions to Z-tests in Tableau, my approach adds critical safeguards for business users:

1.  **Minimum Sample Size Guardrails:** Most dashboards show significance (p < 0.05) even when sample sizes are too small, leading to premature conclusions. My dashboard explicitly visualizes the "Minimum Sample Size" line, warning users if the test is not yet mature.
2.  **Native Implementation:** By avoiding Python/R integrations, this solution works seamlessly on Tableau Public and requires no complex server-side configuration.
3.  **Advanced Configuration:** Users can adjust parameters like Confidence Level and MDE directly in the UI to see how they impact the required sample size and significance.

### Business Value

For businesses, this tool bridges the gap between raw data and statistical rigor. It provides accurate A/B testing by:
* **Reducing Risk:** Prevents rolling out "winning" features that are actually neutral or harmful.
* **Saving Time:** Automates complex calculations that analysts usually perform manually in Excel or R.
* **Standardizing Decisions:** Provides a consistent framework for evaluating experiments across the organization.

<br>

<div class = "github">
    <div class = "github-link">
        Visit the dashboard on
        <a href='https://public.tableau.com/app/profile/bruno.ponne/viz/Click-throughRateABTest/ABTestDashboard' target="_blank"> Tableau Public.</a>
    </div>
</div>