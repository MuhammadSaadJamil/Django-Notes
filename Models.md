# Model
## verbose_name
`sites = models.ManyToManyField(Site, verbose_name="list of sites")`
## Relationships
1. ManyToMany
2. ManyToOne ( ForeignKey )
3. OneToOne

## Through relation

> class Person(models.Model):
>>    name = models.CharField(max_length=128)
___
>class Group(models.Model):
>>    name = models.CharField(max_length=128)\
>>    members = models.ManyToManyField(Person,        through='Membership')
___
`class Membership(models.Model):
    person = models.ForeignKey(Person, on_delete=models.CASCADE)
    group = models.ForeignKey(Group, on_delete=models.CASCADE)
    date_joined = models.DateField()
    invite_reason = models.CharField(max_length=64)
`

### Examples
> ringo = Person.objects.create(name="Ringo Starr")\
> paul = Person.objects.create(name="Paul McCartney")\
> beatles = Group.objects.create(name="The Beatles")\
> m1 = Membership(person=ringo, group=beatles,
>>     date_joined=date(1962, 8, 16),
>>     invite_reason="Needed a new drummer.")
> m1.save()\
> beatles.members.all()

## ManyToMany:
1. add()
2. create()
3. set()
4. remove()
5. clear()
4. related_name = **for reverse relation** , related_query_name = **for query**

## Model methods
1. \__str\__()
2. \__repr\__()
3. get_absolute_path()

## Model Inheritence:
1. Abstract Base Class Inheritence
2. Multi-table Inheritence
3. Proxy Inheritence

### Abstract Base Class Inheritence
1. Table for parent is not created and no manager is assigned to parent as parent is considered a abstract class
` add abstract = True  in meta class`
2. Meta is inherited by child by default
3. Explicit inheritence of meta can be defined as `class Meta(CommonInfo.Meta)`
4. Multiple meta inheritence mut be explicitly defined
### Multi-table Inheritence
1. Table created for parent as well
2. OneToOne relation with parent
### Proxy
1. Place holder for same table
2. used to override methods without changing the original
3. declare by ` proxy=True in meta class `

## Model Meta
1. abstract
2. app_label
3. base_manager_name **default objects**
4. db_table
5. default_related_name **default model_set**
6. get_latest_by ( usually date ) -> latest(), earliest()
7. managed ( managed by django )
8. order_with_respect_to = 'string' e.g one question many anwsers | question.get_anwser_order() + question.set_anwser_order() | anwser.get_next_in_order() + anwser.get_previous_in_order()
9. ordering = ["name", "-createdAt"]
10. proxy
11. unique_together = ["", ""]
12. verbose_name
13. verbose_name_plural

## Model Fields
1. UUIDField | id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)
2. ImageField
3. FileField
4. slugField
5. TextField
6. CharField
7. integerField
8. FloatField
9. DecimalField
10. DateField
11. DatetimeField
12. JSONField
13. AutoField
14. BigAutoField
15. ForeignKeyField
16. OneToOneField
17. ManyToManyField

## ORM
1. get() | DoesNotExist, MultipleObjectsReturned
2. filter()
3. all()
4. exclude()
5. order_by()
6. asc()
7. desc()
8. reverse()
9. distinct()
10. qs.union(qs1, qs2)
11. qs.intersection(qs1, qs2)
12. qs.difference(qs1, qs2)
13. Entry.objects.select_related('blog').get('id') -> get foreign key data as well. | performance booster | OneToOne and foreign key | does heavy work in SQL | single SQL
14. prefetch_related() | manyToMany, ManyToOne | multiple queries | join in python
15. Entry.objects.defer("headline", "body") | Donot retrieve
16. Person.objects.only("name") |get only this
17. create()
18. get_or_create() | obj, created = Person.objects.get_or_create()
19. update_or_create()
20. bulk_create() | bulk_create( obj1, obj2, ...) | no ManyToMany
21. bulk_update()
22. count()
23. latest()
24. earliest()
25. first()
26. last()
27. exists()
28. contains()
29. update()
30. delete()

### Field LookUp
1. id__exact
2. name__iexact | case insensitive exact match
3. name__contains
4. name__icontains
5. name__in = ["a","b","c"]
6. id__gt = 14
7. id__gte
8. id__lt
9. id__lte
10. name__startswith = "AA"
11. name__istartswith = "AA" | case insensitive
12. name__endswith = "AA"
13. name__iendswith = "AA" | case insensitive
14. date__range=(start_date, end_date)
15. date__year=2005
16. date__month=12
17. date__day=3
18. date__week=52
19. date__week_day=2
20. date__quarter=2
21. date__time=datetime.time(14, 30)
22. time__hour=5
23. time__minute=46
24. time__second=2
25. date__isnull=True
26. title__regex=r'^(An?|The) +'
27. title__iregex=r'^(an?|the) +'

## Copying object
blog.pk = None
blog._state.adding = True
blog.save()

## aggeregations
1. Book.objects.all().aggregate(Avg('price'))
2. annotate for each item of queryset. | calculating number of answers for weach question. | `Question.objects.annotate(choice_count=Count('choice'))`
3. aggregate for whole queryset. | calculating total number of answers. | `Choice.objects.aggregate(num_votes=Sum('votes'))`

