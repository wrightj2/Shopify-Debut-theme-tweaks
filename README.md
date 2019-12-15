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

<ins>TO CONTROL THE NUMBER OF COLUMNS USED IN DROPDOWN MENU FOR A SPECIFIC NAVLABEL</ins>

Add the following code to product-template.liquid
```
/*================ Make Fishing menu multi-column (Jon) ================*/
#SiteNavLabel-fishing { width: auto; }
#SiteNavLabel-fishing  ul { column-count: 4; }
#SiteNavLabel-fishing  ul li {-webkit-column-break-inside: avoid;page-break-inside: avoid;    break-inside: avoid; }
```
<ins>TO ADD BREADCRUMBS</ins>

Follow instructions here https://help.shopify.com/en/themes/customization/navigation/add-breadcrumbs

Also add the following CSS to theme.scss.liquid
```
.breadcrumb {
 padding-left: 92px;
 padding-top: 5px;
 font-size: small;
}
```
More here re Structured Data for Breadcrumbs

https://www.shopify.co.uk/partners/blog/breadcrumb-navigation
https://gist.github.com/mirceapiturca/9be3186b607922e0a1b9#file-shopify-breadcrumb-liquid-rich-snippets
