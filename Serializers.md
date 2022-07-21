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
