# Shopify Liquid Components

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Shopify](https://img.shields.io/badge/Shopify-Liquid-green.svg)
![Status](https://img.shields.io/badge/status-production--ready-brightgreen.svg)
![Zero Apps](https://img.shields.io/badge/apps-zero%20dependencies-brightgreen.svg)

A production-ready library of custom Shopify Liquid components. Built natively for stores that need performance without third party app overhead. No monthly fees. No bloat. Just clean Liquid code that converts.

---

## The Problem This Solves

Most Shopify stores install apps for every feature. Sticky cart app. Variant selector app. Upsell app. Each one adds JavaScript overhead, slows your store, and costs monthly fees. This library replaces all of that with native Liquid components hardcoded directly into your theme.

---

## Components

```mermaid
graph TD
    A[Shopify Theme] --> B[Sticky Cart Drawer]
    A --> C[Smart Variant Selector]
    A --> D[Countdown Timer]
    A --> E[Progress Bar Upsell]
    A --> F[Conditional Metafield Display]
    B --> G[Zero App Dependencies]
    C --> G
    D --> G
    E --> G
    F --> G
```

---

## Component Library

| Component | Description | Replaces |
|---|---|---|
| Sticky Cart Drawer | AJAX slide out cart with upsells | $19/mo app |
| Smart Variant Selector | Image swapping variant buttons | $15/mo app |
| Countdown Timer | Urgency timer tied to metafields | $9/mo app |
| Progress Bar Upsell | Free shipping progress indicator | $12/mo app |
| Conditional Metafield Display | Dynamic content by product type | Custom dev |

---

## Sample Component

**Smart Variant Selector:**
```liquid
{% assign current_variant = product.selected_or_first_available_variant %}

<div class="variant-selector">
  {% for option in product.options_with_values %}
    <div class="option-group">
      <label>{{ option.name }}</label>
      <div class="option-values">
        {% for value in option.values %}
          {% assign variant_available = false %}
          {% for variant in product.variants %}
            {% if variant.option1 == value and variant.available %}
              {% assign variant_available = true %}
            {% endif %}
          {% endfor %}
          <button
            class="option-btn {% if variant_available == false %}sold-out{% endif %}"
            data-value="{{ value }}"
            data-option="{{ option.name }}">
            {{ value }}
          </button>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
</div>
```

---

## Quick Start

```bash
git clone https://github.com/Waynelynx12/shopify-liquid-components.git
```

Copy any component snippet into your Shopify theme under **Online Store > Themes > Edit Code > Snippets** and render it using:

```liquid
{% render 'component-name', product: product %}
```

---

## Built By

Sheriff Wayne, Growth Engineer and Shopify Technical Specialist. I build native Liquid components for ecommerce stores that need conversion features without app dependency or monthly overhead.
