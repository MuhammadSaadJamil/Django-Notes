# Validator
1. UniqueValidator\
validators=[UniqueValidator(queryset=BlogPost.objects.all())]
2. UniqueTogetherValidator\
validators = [\
            UniqueTogetherValidator(\
                queryset=ToDoItem.objects.all(),\
                fields=['list', 'position']\
            )
        ]
3. UniqueForDateValidator, UniqueForMonthValidator, UniqueForYearValidator \
UniqueForYearValidator(\
                queryset=BlogPostItem.objects.all(),\
                field='slug',\
                date_field='published'\
            )
