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

## Model Serializer:
### Meta
1. depth = 1
2. read_only_fields = ['account_name']

