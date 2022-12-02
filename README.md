#### models:

```from django.db import models

class Category(models.Model):
    name = models.CharField(max_length=255)

    def __str__(self):
        return self.name


class Product(models.Model):
    name = models.CharField(max_length=255)
    category = models.ForeignKey(
        Category, 
        on_delete=models.CASCADE,
        related_name='products',
        blank=True,
        null=True
    )

    def __str__(self):
        return self.name 
```

#### content:


![Alt text](tables.jpg?raw=true "Optional Title")

#### shell:


```>>> from shop.models import *
>>> p = Product.objects.get(id=1)
>>> p.name
'iPhone X'
>>> p.category
<Category: Apple>
>>> p.category.products.all()
<QuerySet [<Product: iPhone X>, <Product: iPhone 8>, <Product: iPhone 9>, <Product: iPhone 11>, <Product: iPhone 12 ProMax>]>
>>> c = Category.objects.get(id=1)
>>> c.name
'Apple'
>>> c.products.all()
<QuerySet [<Product: iPhone X>, <Product: iPhone 8>, <Product: iPhone 9>, <Product: iPhone 11>, <Product: iPhone 12 ProMax>]>
```