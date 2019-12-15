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

But slightly amend the code to correct positioning to align with page-width by using <div class="page-width">

```
{% unless template == 'index' or template == 'cart' or template == 'list-collections' %}
<nav class="breadcrumb" role="navigation" aria-label="breadcrumbs">
  <div class="page-width">
  <a href="/" title="Home">Home</a>
  {% if template contains 'page' %}
    <span aria-hidden="true">&rsaquo;</span>
    <span>{{ page.title }}</span>
  {% elsif template contains 'product' %}
    {% if collection.url %}
      <span aria-hidden="true">&rsaquo;</span>
      {{ collection.title | link_to: collection.url }}
    {% endif %}
    <span aria-hidden="true">&rsaquo;</span>
    <span>{{ product.title }}</span>
  {% elsif template contains 'collection' and collection.handle %}
    <span aria-hidden="true">&rsaquo;</span>
    {% if current_tags %}
      {% capture url %}/collections/{{ collection.handle }}{% endcapture %}
      {{ collection.title | link_to: url }}
      <span aria-hidden="true">&rsaquo;</span>
      <span>{{ current_tags | join: " + " }}</span>
    {% else %}
      <span>{{ collection.title }}</span>
    {% endif %}
  {% elsif template == 'blog' %}
    <span aria-hidden="true">&rsaquo;</span>
    {% if current_tags %}
      {{ blog.title | link_to: blog.url }}
      <span aria-hidden="true">&rsaquo;</span>
      <span>{{ current_tags | join: " + " }}</span>
    {% else %}
    <span>{{ blog.title }}</span>
    {% endif %}
  {% elsif template == 'article' %}
    <span aria-hidden="true">&rsaquo;</span>
    {{ blog.title | link_to: blog.url }}
    <span aria-hidden="true">&rsaquo;</span>
    <span>{{ article.title }}</span>
  {% else %}
   <span aria-hidden="true">&rsaquo;</span>
   <span>{{ page_title }}</span>
  {% endif %}
</nav>
{% endunless %}
```

Also add the following CSS to theme.scss.liquid
```
.breadcrumb {
 padding-top: 2px;
 font-size: small;
}

.breadcrumb {
  color: inherit;
  font-weight: normal;
  text-decoration: none;
}

.breadcrumb :hover,
.breadcrumb focus {
  text-decoration: underline;
}
```
More here re Structured Data for Breadcrumbs

https://www.shopify.co.uk/partners/blog/breadcrumb-navigation
https://gist.github.com/mirceapiturca/9be3186b607922e0a1b9#file-shopify-breadcrumb-liquid-rich-snippets
