# Authentication and Authorization

## Functions
1. create_user()
2. authenticate(username='', password='')
3. user.groups.add()
4. user.user_permissions.add()
5. group.permissions.add()
6. content_type = ContentType.objects.get_for_model(BlogPost) `permission = Permission.objects.create(\
    codename='can_publish',\
    name='Can Publish Posts',\
    content_type=content_type,\
)`
7.
