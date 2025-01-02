``` python
from django.urls import path
from .views import TerrainAPIView

urlpatterns = [
    path('terrain/', TerrainAPIView.as_view()),
    path('terrain/<int:pk>/', TerrainAPIView.as_view()),
    path('editor/', editor_view),

]

```
