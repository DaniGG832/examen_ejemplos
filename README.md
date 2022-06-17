# examen_ejemplos

- Borrar coleccion  -->    $carritos->each->delete();

- tabla intermedia // attach/detach -->  $articulo->autores()->sync($request->autores);

- delete con contrains
          if (!Nota::all()->contains($alumno->id)) {
               $alumno->delete();
               return redirect()->route('alumnos.index')->with('success', 'alumno borrado correctamente');
          }

- groupBy  --> $cceemasalto = $ccees->where('alumno_id', $alumno->id)->groupBy('ccee_id');

- 
