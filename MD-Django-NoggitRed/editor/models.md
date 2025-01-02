``` python
from django.db import models

# Main ADTFile model representing the overall file structure
class ADTFile(models.Model):
    version = models.IntegerField()  # Version information
    header = models.OneToOneField('MHDR', on_delete=models.CASCADE)  # Header information
    textures = models.ManyToManyField('MTEX')  # Texture lists
    models = models.ManyToManyField('MMDX')  # Model references
    objects = models.ManyToManyField('MDDF')  # Object placements

    class Meta:
        verbose_name = 'ADT File'
        verbose_name_plural = 'ADT Files'

    def __str__(self):
        return f"ADT File (Version: {self.version})"

# Model for MVER (version information)
class MVER(models.Model):
    version = models.IntegerField()  # Version information

    def __str__(self):
        return f"MVER (Version: {self.version})"

# Model for MHDR (header)
class MHDR(models.Model):
    offset = models.IntegerField()  # Offset information

    def __str__(self):
        return f"MHDR (Offset: {self.offset})"

# Model for MTEX (texture lists)
class MTEX(models.Model):
    texture_path = models.CharField(max_length=255)  # Path to texture file

    def __str__(self):
        return f"MTEX (Texture: {self.texture_path})"

# Model for MMDX (model references)
class MMDX(models.Model):
    model_path = models.CharField(max_length=255)  # Path to model file

    def __str__(self):
        return f"MMDX (Model: {self.model_path})"

# Model for MMID (model indices)
class MMID(models.Model):
    index = models.IntegerField()  # Index information

    def __str__(self):
        return f"MMID (Index: {self.index})"

# Model for MWMO (WMO references)
class MWMO(models.Model):
    wmo_path = models.CharField(max_length=255)  # Path to WMO file

    def __str__(self):
        return f"MWMO (WMO: {self.wmo_path})"

# Model for MWID (WMO indices)
class MWID(models.Model):
    index = models.IntegerField()  # Index information

    def __str__(self):
        return f"MWID (Index: {self.index})"

# Model for MDDF (object placements)
class MDDF(models.Model):
    model = models.ForeignKey(MMDX, on_delete=models.CASCADE)  # Reference to model
    position_x = models.FloatField()  # X coordinate
    position_y = models.FloatField()  # Y coordinate
    position_z = models.FloatField()  # Z coordinate
    rotation_x = models.FloatField()  # Rotation around X-axis
    rotation_y = models.FloatField()  # Rotation around Y-axis
    rotation_z = models.FloatField()  # Rotation around Z-axis

    def __str__(self):
        return f"MDDF (Model: {self.model}, Position: ({self.position_x}, {self.position_y}, {self.position_z}))"

# Model for MCNK (map chunks)
class MCNK(models.Model):
    adt_file = models.ForeignKey(ADTFile, on_delete=models.CASCADE)  # Reference to ADT file
    chunk_x = models.IntegerField()  # Chunk X coordinate
    chunk_y = models.IntegerField()  # Chunk Y coordinate

    def __str__(self):
        return f"MCNK (Chunk: ({self.chunk_x}, {self.chunk_y}))"

# Model to represent the coordinate system
class CoordinateSystem(models.Model):
    x = models.FloatField()  # X coordinate (north)
    y = models.FloatField()  # Y coordinate (west)
    z = models.FloatField()  # Z coordinate (height)

    def __str__(self):
        return f"Coordinate (X: {self.x}, Y: {self.y}, Z: {self.z})"

# Model to represent the map structure
class MapStructure(models.Model):
    adt_files = models.ManyToManyField(ADTFile)  # References to ADT files
    block_x = models.IntegerField()  # Block X coordinate
    block_y = models.IntegerField()  # Block Y coordinate

    def __str__(self):
        return f"Map Block (Block: ({self.block_x}, {self.block_y}))"


```
