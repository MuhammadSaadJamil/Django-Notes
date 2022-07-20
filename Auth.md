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
7. request.user.is_authenticated
8. user = authenticate(request, username=username, password=password)\
login(request, user)
9. logout(request)
10. @login_required(redirect_field_name='my_redirect_field')
11. LoginRequiredMixin
12. request.user.email.endswith('@example.com')
13. @user_passes_test(email_check)\
`def email_check(user):
    return user.email.endswith('@example.com')`
14. UserPassesTestMixin -> test_func
15. permission_required(perm, login_url=None, raise_exception=False)
16. PermissionRequiredMixin -> permission_required = '', permission_required = ('','')
17. AccessMixin -> login_url, permission_denied_message, redirect_field_name, raise_exception
18. update_session_auth_hash(request, form.user)
