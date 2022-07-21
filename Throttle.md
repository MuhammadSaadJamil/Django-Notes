# Throttle
1. REST_FRAMEWORK = {\
    'DEFAULT_THROTTLE_CLASSES': [\
        'rest_framework.throttling.AnonRateThrottle',\
        'rest_framework.throttling.UserRateThrottle'\
    ],\
    'DEFAULT_THROTTLE_RATES': {\
        'anon': '100/day',\
        'user': '1000/day'\
    }\
}
2. The rate descriptions used in DEFAULT_THROTTLE_RATES may include second, minute, hour or day as the throttle period.
3. AnonRateThrottle -> DEFAULT_THROTTLE_RATES['anon']
4. UserRateThrottle -> DEFAULT_THROTTLE_RATES['user']\
class BurstRateThrottle(UserRateThrottle):\
    scope = 'burst'\
 'DEFAULT_THROTTLE_RATES': {\
        'burst': '60/min',\
        'sustained': '1000/day'\
    }
