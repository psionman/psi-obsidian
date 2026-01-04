## Output dates for js
tags: #dates-for-js
```python
user = get_user_from_username(params.user_query)
last_activity_iso = (
	user.last_activity
	.replace(microsecond=(user.last_activity.microsecond // 1000) * 1000)  # milliseconds
	.isoformat()
	.replace('+00:00', 'Z')  # if it's UTC-aware
)
return {
	'logged_in': user.logged_in,
	'last_activity': last_activity_iso,
}
```