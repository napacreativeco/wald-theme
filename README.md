#WALD THEME

## Notes

**Taken from blog.liquid:**
{% comment %}
    Let's extract a blog image.
    We will look for an image in the excerpt first, and in the blog post itself second.
    We will remove the image suffix to grab as big an image as we can.
{% endcomment %}

{% assign article_has_image = false %}
{% assign img_tag = '<' | append: 'img' %}
{% if article.excerpt_or_content contains img_tag %}
    {% assign src = article.excerpt_or_content | split: 'src="' %}
    {% assign src = src[1] | split: '"' | first %}
    {% if src %}
    {% assign article_has_image = true %}
    {% assign image_src = src | replace: '_small', '' | replace: '_compact', '' | replace: '_medium', '' | replace: '_large', '' | replace: '_grande', '' %}
    {% endif %}
{% endif %}  