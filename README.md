# Shopify-Debut-theme-tweaks

<ins>TO SHOW A DISCOUNT 'BANNER' ONLY ON SPECIFIC PRODUCT PAGES</ins>
Add the following code to product-template.liquid
```
{% for collection in product.collections %}
   {% if collection.title == 'YOUR COLLECTION NAME' %}
      <div class="collection-banner-container">
         <span class="collection-banner">YOUR TEXT</span>
      </div>
   {% endif %}
{% endfor %}
```
