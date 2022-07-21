# Serializers

## Properties:
1. Convert data to native python
2. .create() .update()
3. serializer.save(extra='') => stored in **validated_data**
4. validate_**FIELD**()  => field validation
5. validate(self, data) => validate object
6. validators => function for validation => def validator_(data)
7. serializer(instance=Test, data={'comment':'test'}, partial=True)
8. class CommentSerializer(serializers.Serializer):\
    user = UserSerializer(required=False)\
    edits = EditItemSerializer(many=True)\
    content = serializers.CharField(max_length=200)\
    created = serializers.DateTimeField()
9. serializer.errors
10. serializer(data, many=True)
11. serializer(data, context={'key': 'value'})
12. ListSerializer -> many=True\
 i. allow_empty\
 ii. min_length\
 iii. max_length

## Model Serializer:
1. get_field() --> Depreciated
2. get_pk_field() --> Depreciated
### Meta
1. depth = 1
2. read_only_fields = ['account_name']
3. list_serializer_class

## Base Serializer:
1. to_representation
2. to_internal_value


## Core args
1. read_only
2. write_only
3. required
4. default
5. allow_null
6. source -> what should be the data **e.g 'user.email'**
7. validators -> []
8. label
9. help_text
10. initial
11. style -> style={'input_type': 'password'}

## Fields:
1. BooleanField
2. NullBooleanField
3. CharField -> CharField(max_length=None, min_length=None, allow_blank=False, trim_whitespace=True)
4. EmailField
5. RegexField -> RegexField(regex, max_length=None, min_length=None, allow_blank=False)
6. SlugField
7. URLField
8. UUIDField -> UUIDField(format='hex_verbose')
9. FilePathField -> FilePathField(path, match=None, recursive=False, allow_files=True, allow_folders=False, required=None, **kwargs)
10. IPAddressField
11. IntegerField
12. FloatField
13. DecimalField
14. DateTimeField -> DateTimeField(format=api_settings.DATETIME_FORMAT, input_formats=None, default_timezone=None)
15. DateField -> DateField(format=api_settings.DATE_FORMAT, input_formats=None)
16. TimeField -> TimeField(format=api_settings.TIME_FORMAT, input_formats=None)
17. DurationField -> DurationField(max_value=None, min_value=None)
18. ChoiceField(choices)
19. MultipleChoiceField(choices)
20. FileField(max_length=None, allow_empty_file=False, use_url=UPLOADED_FILES_USE_URL)
21. ImageField(max_length=None, allow_empty_file=False, use_url=UPLOADED_FILES_USE_URL)
22. JSONField(binary, encoder)

## Relation Fields
1. StringRelatedField
2. PrimaryKeyRelatedField
3. HyperlinkedRelatedField(view_name='track-detail')


## Notes:
1. Nested serializers can be used but are read-only by default. To use them override create, update method in parent
2. You can add related name by yourself ( reverse relations )



