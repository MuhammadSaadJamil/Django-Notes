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


