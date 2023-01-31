

# Django Queryset



### All


#### All() is used to return all the objects of the given model. It returns a queryset containing all the objects of the model.

```python

User.objects.all()

```

### Filter

#### filter() is used to return the filtered objects of the given model. It returns a queryset containing all the objects of the model.

```python
 
User.objects.filter(username='root')
# OR
User.objects.filter(username='root').filter(password='123456')


```

### Exclude

#### exclude() is used to return the filtered objects of the given model. It returns a queryset containing all the objects of the model.

```python

User.objects.exclude(username='root')
```


### order_by

#### order_by() is used to return the filtered objects of the given model. It returns a queryset containing all the objects of the model.

```python

User.objects.order_by('username')   # it will return the queryset in ascending order

```

### reverse

#### reverse() is used to return the objects in reverse order.

```python

User.objects.order_by('username').reverse()   # it will return the queryset in descending order

```


### count

#### count() is used to return the number of objects in the queryset.

```python

User.objects.count()

```

### distinct

#### distinct() is used to return the distinct objects in the queryset.

```python

User.objects.distinct()

```

### values

#### values() is used to return the values of the given field in the queryset.

```python

User.objects.values('username')  # it will return the queryset with only username field

User.objects.values()  # it will return the queryset with all the fields in dictionary format while values_list() will return the queryset with all the fields in tuple format

```

### values_list

#### values_list() is used to return the values of the given field in the queryset.

```python

User.objects.values_list('username')

```

### exists

#### exists() is used to return True if the queryset is not empty.

```python

Users.objects.filter(username='root').exists()

```


### latest

#### latest() is used to return the latest object of the queryset. If the queryset is empty, it returns None. Same but opposite to earliest().

```python

User.objects.filter(username='root').latest()

```

### earliest

#### earliest() is used to return the earliest object of the queryset. If the queryset is empty, it returns None. Same but opposite to latest().

```python

Users.objects.filter(username='root').earliest()

```

### delete

#### delete() is used to delete the objects of the queryset.

```python

Users.objects.filter(username='root').delete()

```

### update

#### update() is used to update the objects of the queryset.

```python

User.objects.update(username='root')  # it will update all the objects of the queryset


```


### create

#### create() is used to create the objects of the queryset.

```python

Users.objects.create(username='root', password='123456')

```

### get_or_create

#### get_or_create() is used to create the objects of the queryset. it is different from create() in a way that it will not create the object if it already exists.


```python

Users.objects.get_or_create(username='root', password='123456')

```

### update_or_create

#### update_or_create() is used to update the objects of the queryset. it is different from update() in a way that it will not update the object if it does not exists.

```python

Users.objects.update_or_create(username='root', password='123456')

```

### bulk_create

#### bulk_create() is used to create the objects of the queryset. it is different from create() in a way that it will create the objects in bulk.


```python


Users.objects.bulk_create([
    DjangoModel(username="" , password=""),
    DjangoModel(username="" , password=""),
])


```


### bulk_update

#### bulk_update() is used to update the objects of the queryset. it is different from update() in a way that it will update the objects in bulk.


```python

# DjangoModel is model name

Users.objects.bulk_update([
    DjangoModel(username="" , password=""),
    DjangoModel(username="" , password=""),
])


```

### aggregate

#### aggregate() is used to aggregate the objects of the queryset. it is used to perform aggregate functions like sum, avg, max, min, count.


```python
from django.db.models import Avg , Sum , Max , Min , Count

Users.objects.aggregate(Sum('age'))


```


### annotate

#### annotate() is used to annotate the objects of the queryset. it is used to perform annotate functions like sum, avg, max, min, count.

```python

from django.db.models import Avg , Sum , Max , Min , Count

Users.objects.annotate(Sum('age'))

```

### first


#### first() is used to return the first object of the queryset. If the queryset is empty, it returns None. Same but opposite to last().

```python

User.objects.filter(username='root').first()
# OR
User.objects.all().first()


```

### get


#### get() is used to return the first object of the queryset. If the queryset is empty, it raises DoesNotExist exception. also if the queryset has more than one object, it raises MultipleObjectsReturned exception.


```python

User.objects.get(username='root')
#  mainly used with Primary key

```


### in_bulk

#### in_bulk() is used to return the objects of the queryset in bulk. it returns a dictionary with the primary key as the key and the object as the value.

```python

User.objects.in_bulk([PK1, PK2, PK3])
#  Primary key is passed as a list , works as multiple get() function


```


### explain

#### explain() is used to return the explaination of the queryset.

```python

User.objects.explain()


#  Output

# '2 0 0 SCAN TABLE app1_users'

    # 2: The number of rows that the query scanned.
    # 0: The number of rows returned by the query.
    # 0: The number of cache hits that the query had.
    # SCAN TABLE: The type of operation being performed, in this case a full table scan.
    # app1_users: The name of the table being scanned, in this case the User model is stored in the app1_users table in the database.



```

### contains




### prefetch_related

#### prefetch_related is a method in Django ORM (Object-Relational Mapping) that allows you to fetch related objects for multiple objects in one query, reducing the number of database queries, improving performance. It can be used on a queryset to optimize database access when retrieving related objects.



```python

books = Book.objects.all().prefetch_related('authors')


This will fetch all books and their related authors in a single query, rather than making one query per book to fetch its authors.

```

### select_related






