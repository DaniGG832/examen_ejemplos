# examen_ejemplos

- Borrar coleccion  -->    $carritos->each->delete();

- tabla intermedia // attach/detach -->  $articulo->autores()->sync($request->autores);

- groupBy  --> $cceemasalto = $ccees->where('alumno_id', $alumno->id)->groupBy('ccee_id');

- concatenar en una coleccion --> $coleccionNotasMasAltas = $coleccionNotasMasAltas->concat([$notamasalta->first()]);

- nota mas alta max  -->  $notaMasAlta = $ccee->notas->max('nota');

- diferente --> $notasDiff =Nota::where('alumno_id','<>',4)->get();

- acceder usuario {{(Auth::user()->name)}} /// $reservas = Auth::user()->reservas;

- ordenar --   $albumes = Album::ordenar('anyo')->get(); ///
               $ccees = Nota::orderBy('nota', 'desc')->get();  // 
               $cceemasalto = $ccees->where('alumno_id', $alumno->id)->groupBy('ccee_id');

- can:solo-admin(monografias alonso)

          Route::resource('/monografias', MonografiaController::class)->middleware(['auth', 'can:solo-admin']);
    
          - (App\Providers\AuthServiceProvider)
          - use App\Models\User;
            use Illuminate\Auth\Access\Response;
            use Illuminate\Foundation\Support\Providers\AuthServiceProvider as ServiceProvider;
            use Illuminate\Support\Facades\Gate;
           
           public function boot()
    {
        $this->registerPolicies();

        Gate::define('solo-admin', function (User $user) {
            return $user->name == 'admin'
                ? Response::allow()
                : Response::deny('Debes ser administrador');
        });
    }
            
    
-

-- delete con contrains
          if (!Nota::all()->contains($alumno->id)) {
               $alumno->delete();
               return redirect()->route('alumnos.index')->with('success', 'alumno borrado correctamente');
          }
          
          
           if (!Nota::all()->contains($ccee->id)) {
            $ccee->delete();
            return redirect()->route('ccees.index')->with('success','ccee borrado correctamente');
        
        }

        return redirect()->route('ccees.index')->with('error','No se puede borrar un ccee con notas asociadas');

    }
 

