# Dyode-Liquid-Challenge

#### 1. Describe how you would make a line of text in a homepage section editable from theme customization and how you would access this in liquid.

Create a section schema with a text setting, accessing the value of that setting in the markup above

```liquid
<p>{{ section.settings.hp_text }}</p>

{% schema %}
{
  "name": "Homepage Section",
  "settings": [
    {
      "type": "text",
      "id": "hp_text",
      "label": "Homepage Text"
    }
  ]
}
{% endschema %}
```

#### 2. How would you add the collection featured image as a banner on the collection liquid template?

Using the below liquid code to dynamically pull in the collection image, but probably at different resolutions to make a responsive banner.

```liquid
{{ collection.image | img_url: 'master' }}
```

#### 3. Using liquid code and HTML, create a simple pagination container, "< 1 2 ... 5 >".

```liquid
<section>
{% paginate collection.products by 6 %}
  {% for product in collection.products %}
    <!-- render product card -->
  {% endfor %}
  
  {{ paginate | default_pagination }}
{% endpaginate %}
</section
```

#### 4. Using liquid code, access the product named "Blue T-Shirt". Store the id, title, handle, price, url, and image in variables.

```liquid
{% liquid
assign productHandle = "Blue T-Shirt" | handleize
assign productData = all_products[productHandle]

assign id = productData.id
assign title = productData.title
assign handle = productData.handle
assign price = productData.price
assign url = productData.url
assign image = productData.featured_image
%}

```

#### 5. Using liquid code, create a key:value array using the list below. Loop through the array. Upon key type, store the value in a variable to be used later:
- fruit:apple
- vegetable:carrot
- cloth:t-shirt
- denim:jeans

```liquid
{% liquid
  assign pairs = "fruit:apple,vegetable:carrot,cloth:t-shirt,denim:jeans" | split: ','
  
  for pair in pairs
    assign splitPair = pair | split: ':'
    assign key = splitPair[0]
    
    if ( some key based condition ) 
      assign value = splitPair[1]
    endif 
  endfor
%}
```
