``` python
from django.shortcuts import render
from rest_framework.views import APIView
from rest_framework.response import Response
from rest_framework import status
from .models import Terrain

class TerrainAPIView(APIView):
    def get(self, request, pk=None):
        if pk:
            terrain = Terrain.objects.get(pk=pk)
            return Response(terrain.data)
        terrains = Terrain.objects.all().values('id', 'name')
        return Response(list(terrains))

    def post(self, request):
        name = request.data.get('name', 'New Terrain')
        data = request.data.get('data', {})
        terrain = Terrain.objects.create(name=name, data=data)
        return Response({'id': terrain.id, 'name': terrain.name}, status=status.HTTP_201_CREATED)


def editor_view(request):
    return render(request, 'editor/editor.html')

```
