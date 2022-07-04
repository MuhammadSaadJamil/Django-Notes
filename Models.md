# Model
## verbose_name
`sites = models.ManyToManyField(Site, verbose_name="list of sites")`
## Relationships
1. ManyToMany
2. ManyToOne ( ForeignKey )
3. OneToOne

## Through relation
`
class Person(models.Model):
    name = models.CharField(max_length=128)`
___
`class Group(models.Model):
    name = models.CharField(max_length=128)
    members = models.ManyToManyField(Person, through='Membership')`
___
`class Membership(models.Model):
    person = models.ForeignKey(Person, on_delete=models.CASCADE)
    group = models.ForeignKey(Group, on_delete=models.CASCADE)
    date_joined = models.DateField()
    invite_reason = models.CharField(max_length=64)
`

### Examples
ringo = Person.objects.create(name="Ringo Starr")
> paul = Person.objects.create(name="Paul McCartney")
> beatles = Group.objects.create(name="The Beatles")
> m1 = Membership(person=ringo, group=beatles,
>>     date_joined=date(1962, 8, 16),
>>     invite_reason="Needed a new drummer.")
> m1.save()
> beatles.members.all()
