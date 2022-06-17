# plantilla

editorial monografias index, enlaces y botones

# titulo

<div class="flex flex-col items-center mt-4">
        <h1 class="mb-4 text-2xl font-semibold">Articulos</h1>

    </div>

# enlaces 


    <div
        class="outline-none mr-1 mb-1 px-3 py-1 bg-transprent text-xs font-bold text-blue-500 uppercase focus:outline-none">

        <a href="{{ '/monografias' }}"> ir a monografias</a>
    </div>

    <div
        class="outline-none mr-1 mb-1 px-3 py-1 bg-transprent text-xs font-bold text-blue-500 uppercase focus:outline-none">

        <a href="{{ '/autores' }}"> ir a autores</a>
    </div>

    <a href="/articulos/create" class="mt-4 text-blue-900 hover:underline">Insertar nuevo articulo</a>
    </div>


# index de articulos (tabla)

<div class="border border-gray-200 shadow">
        <table class="table-auto">
            <thead class="bg-blue-300">
                <tr>

                    <th class="px-6 py-2 ">
                        Titulo
                    </th>
                    <th class="px-6 py-2 ">
                        Año
                    </th>
                    <th class="px-6 py-2 ">
                        num_paginas
                    </th>
                </tr>
            </thead>

            <tbody class="bg-blue-100">


                {{-- Para ascendente :$articulos->sortBy('anyo')

                 @foreach ($articulos->sortBy('anyo') as $articulo) --}}

                @foreach ($articulos->sortByDesc('anyo') as $articulo)
                    <tr>

                        <td class="px-6 py-2">{{ $articulo->titulo }}</td>
                        <td class="px-6 py-2">{{ $articulo->anyo }}</td>
                        <td class="px-6 py-2">{{ $articulo->num_paginas }}</td>
                        <td class="px-6 py-4">
                            <a href="{{ route('articulos.show', $articulo, true) }}"
                                class="px-4 py-1 text-sm text-white bg-blue-400 rounded">Mostrar</a>
                        </td>
                        <td class="px-6 py-4">
                            <a href="{{ route('articulos.edit', $articulo, true) }}"
                                class="px-4 py-1 text-sm text-white bg-blue-400 rounded">Editar</a>
                        </td>
                        <td class="px-6 py-4">
                            <form action="{{ route('articulos.destroy', $articulo) }}" method="POST">
                                @csrf
                                @method('DELETE')
                                <button onclick="return confirm('¿Seguro que desea borrar la articulo?')"
                                    class="px-4 py-1 text-sm text-white bg-red-400 rounded"
                                    type="submit">Borrar</button>
                            </form>
                        </td>
                    </tr>
                @endforeach

            </tbody>
        </table>



# index  de alumnos

-  <table class="table text-gray-400 border-separate space-y-6 text-sm">
            <thead class="bg-blue-500 text-white">
              <tr>
                
                <th class="p-3 text-left">ce</th>
                <th class="p-3 text-left">Descrición</th>



                <th class="p-3 text-left">Mostrar</th>
                <th class="p-3 text-left">Editar</th>
                <th class="p-3 text-left">Borrar</th>

              </tr>
            </thead>
            <tbody>
              @foreach ($ccees as $ccee)
                <tr class="bg-blue-200 lg:text-black">
                  <td class="p-3 font-medium capitalize">{{ $ccee->id }}</td>
                  <td class="p-3">
                    <a href="{{ route('ccees.show', $ccee, false) }}">
                      {{ $ccee->ce }}
                    </a>
                  </td>

                  <td class="p-3">
                    <a href="{{ route('ccees.show', $ccee, false) }}">
                      {{ $ccee->descripcion }}
                    </a>
                  </td>

                  <td class="p-3 bg-blue-700 ">
                    <a href="{{ route('ccees.show', $ccee, false) }}"
                      class="text-gray-100 hover:text-green-400 mr-2">
                      <i class="material-icons-outlined text-base">Mostrar</i>
                    </a>
                  </td>

                  <td class="p-3 bg-green-700 ">

                    <a href="{{ route('ccees.edit', $ccee, false) }}"
                      class="text-gray-100 hover:text-green-400 mr-2">
                      <i class="material-icons-outlined text-base">Editar</i>
                    </a>
                  </td>

                  <td class="p-3 bg-red-500 ">
                    <form action="{{ route('ccees.destroy', $ccee, true) }}" method="post">

                      @csrf
                      @method('delete')

                      <button class="text-red-100 hover:text-red-900 mx-2 material-icons-outlined text-base"
                        type="submit">Borrar</button>
                    </form>

                  </td>

                </tr>
              @endforeach

            </tbody>
          </table>

          <div class="flex justify-center">
            <a href="{{ route('ccees.create') }}">
              <button
                class="mt-5 py-1 px-4 text-blue-700 hover:text-white border border-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded text-sm text-center mr-2 mb-2 dark:border-blue-500 dark:text-blue-500 dark:hover:text-white dark:hover:bg-blue-600 dark:focus:ring-blue-800">Añadir
                nuevo ccee</button>
            </a>
