``` python
from django.db import models

class Terrain(models.Model):
    name = models.CharField(max_length=100)
    data = models.JSONField()  # Stocke les données terrain (grille de hauteur, textures)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    def _str_(self):
        return self.name

```
