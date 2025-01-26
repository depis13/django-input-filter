# Django Input Filter

A Django library for creating advanced input filters in admin interfaces.

## Installation

Install the package using pip:

```bash
pip install django-input-filter
```

## Configuration

Add `django_input_filter` to your `INSTALLED_APPS` in `settings.py`:

```python
INSTALLED_APPS = [
    ...
    'django_input_filter',
    ...
]
```

## Usage Example

```python
from django_input_filter import InputFilter

class NameContainsInputFilter(InputFilter):
    title = "Name Contains Filter"
    parameter_name = "name_contains"

    def queryset(self, request, queryset):
        term = self.value()
        if term is None:
            return queryset
        return queryset.filter(name__icontains=term)
```
```python
@admin.register(ModelName)
class ModelNameAdmin(admin.ModelAdmin):
    ...
    list_filter = (
        ...
        NameContainsInputFilter
    )
```
