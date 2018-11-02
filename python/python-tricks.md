# My Python Tricks #

## Autocomplete while programming ##

```
import rlcompleter, readline
readline.parse_and_bind('tab:complete')
```

## Inspect arguments for a method ##

```
import inspect
inspect.getargspec(nova.flavors.list)
```

