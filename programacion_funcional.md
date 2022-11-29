# Universidad de Colima
## Programación Funcional
## Profesor: Walter Alexander Mata Lopez
## *andrea ketzabel madrigal rodriguez*
## 29-11-2022
## 3°B
    
    

### _1. Función Sin Argumentos_
    
    defmodule HolaMundo do
     def mensaje do
    Fundamentos de programación funcional con Erlang y Elixir,
     IO.puts("Hola Mundo")
     end
    end


### _2. Función Con Argumentos_
    defmodule Calculadora do
     def suma(n1,n2) do
     n1 + n2
     end
    end

### _3. Varios Módulos En Un Archivo_
    defmodule Calculadora do
     def suma(n1,n2) do
     n1 + n2
     end
    end
    defmodule Areas do
     def area_cuadrado(l) do
     l*l
     end
    end


### _4. Reglas De Los Módulos_
    # Reglas de los módulos:
    # -Inicia con una letra mayúscula
    # -Se escribe con el estilo CamelCase
    # -Puede consistir en caracteres alfanuméricos, subrayados y puntos (.).
    # -Regularmente se usa para la organización jerárquica de los módulos. 

    defmodule Geometria.Cuadrado do
     def perimetro(l) do
     4*l
     end
    end
    defmodule Geometria.Rectangulo do
     def perimetro(l1,l2) do
     2*l1 + 2*l2
     end
    end


### _5. Otra Forma De Unir Los Módulos_
    defmodule Geometria do
     defmodule Cuadrado do
     def perimetro(l) do
     4*l
     end
     end
     defmodule Rectangulo do
     def perimetro(l1,l2) do
     2*l1 + 2*l2
     end
     end
    end


### _6. Funciones Expresadas_
    defmodule Geometria do
     def perimetro_cuadrado(l), do: 4*l
     def perimetro_rectangulo(l1,l2), do: 2*l1 + 2*l2
    end


### _7. Invocaciones De Una Función Interna_
    defmodule Geometria do
     def perimetro1(l), do: cuadrado(l)
     def perimetro2(l), do: Geometria.cuadrado(l)
     def cuadrado(l), do: 4*l
    end
    ### _8. Visibilidad de Funciones_
    #-Se pueden utilizar funciones privadas con el constructor def
    #-Función Publica y privada 

    defmodule TestPublicoPrivado do
     def funcion_publica(msg) do
     IO.puts("#{msg} publico")
     funcion_privada(msg)
     end
     defp funcion_privada(msg) do
     IO.puts("#{msg} privado")
     end
    end
    TestPublicoPrivado.funcion_publica("este es un mensaje")


### _9. Módulo Geometría_
    defmodule Geometria do
     def perimetro1(l), do: cuadrado(l)
     def perimetro2(l), do: Geometria.cuadrado(l)
     defp cuadrado(l), do: 4*l
    end


### _10. Operador Pipeline_
    # Obtener el cuadrado de la suma de 2 numeros (4 y 5)

    defmodule Operaciones do
     def suma(n1,n2), do: n1 + n2
     def cuadrado(n), do: n * n
    end
### Estructura Código Elixir


### _1. Polimorfismo(Sobrecarga)_
    defmodule Rectangulo do
     def area(l) do
     l * l
     end
     def area(l1,l2) do
     l1 * l2
     end
    end


### _2. Haciendo Que Una Función Dependa De Otra_
    defmodule Calculadora do
     def suma(n) do
     suma(n,0)
     end
     def suma(n1,n2) do
     n1 + n2
     end
    end



### _3. Argumentos Por Defecto_
    defmodule Calculadora do
     def suma(n1,n2 \\ 0) do
     n1 + n2
     end
    end
    #Se puede utilizar cualquier combinación de argumentos por defecto: 
    defmodule Calculadora do
     def funcion(n1,n2 \\ 0, n3 \\ 1, n4, n5 \\ 2) do
     n1 + n2 + n3 + n4 + n5
     end
    end



### _4. Imports_
    import ModuloImportado
    defmodule ModuloMain do
     def main do
     IO.puts("Funcion main")
     funcion_importada("Esta funcion es importada")
     end
    end

    #Creamosel Modulo a importar modsec.ex
    #Escribimos el siguiente codigo: 

    defmodule ModuloImportado do
     def funcion_importada(msg) do
     IO.puts(msg)
     end
    end

    #Si no se quiere importar el modulo, se puede utilizar de manera directa indicando el modulo y la funcion esto es:

    defmodule ModuloMain do
     def main do
     IO.puts("Funcion main")
     ModuloImportado.funcion_importada("Esta funcion es importada")
     end
    end


### _5. Alias_
    defmodule ModuloMain do
     alias ModuloImportado, as: MI

     def main do
     IO.puts("Funcion main")
     MI.funcion_importada("Esta funcion es importada con alias")
     end
    end


### _6. Atributos De Módulo_
    defmodule Geometria do
     @pi 3.141592
     def area(r) do
     r*r*@pi
     end
     def circunferencia(r) do
     2 * r * @pi
     end
    end



### _7. Secuencias De Escape_
    IO.puts("1. Este es un mensaje")
    IO.puts("2. Este es un \n mensaje")
    IO.puts("3. Este es un \"mensaje\"")
    IO.puts("4. Este es un \\mensaje\\")
    IO.puts("5. Este \t es \tun \t mensaje")
    IO.puts("4. Este es un mensaje")


### _8. Concatenación De Cadenas_
    defmodule Cadena do
     def concatenar(cad1, cad2, separador \\ " ") do
     cad1 <> separador <> cad2
     end
    end
    Fundamentos de programación funcional con Erlang y Elixir,
    IO.puts(Cadena.concatenar("Hola", "Mundo"))
    IO.puts(Cadena.concatenar("Hola", "Mundo", "<->"))
    
    ### _9. Funciones_
    defmodule Calculadora do
     def div(_,0) do
     {:error, "No se puede dividir por 0"}
     end
     def div(n1, n2) do
    Fundamentos de programación funcional con Erlang y Elixir,
     {:ok, "El resultado es: #{n1/n2}"}
     end
    end
    IO.inspect(Calculadora.div(5,0))
    IO.inspect(Calculadora.div(5,3))

### _10. Funciones Invertidas_
    defmodule Calculadora do
     def div(n1, n2) do
     {:ok, "El resultado es: #{n1/n2}"}
     end
     def div(_,0) do
     {:error, "No se puede dividir por 0"}
     end
    end
    IO.inspect(Calculadora.div(5,0))
    IO.inspect(Calculadora.div(5,3))

### _11. Guardas_
    defmodule Numero do
     def cero?(0), do: true
     def cero?(n) when is_integer(n), do: false
     def cero?(_), do: "No es entero"
    end

    IO.puts(Numero.cero?(0))
    IO.puts(Numero.cero?(2))
    IO.puts(Numero.cero?("3"))

### _12. Condicionales_
    #EJEMPLO 1

    defmodule Persona1 do
     def sexo(sex) do
     if sex == :m do
     "Masculino"
     else
     "Femenino"
     end
     end
    end

    #EJEMPLO 2

    defmodule Persona2 do
     def sexo(sex) do
     if sex == :m do
     "Masculino"
     else if sex == :f do
     "Femenino"
    Fundamentos de programación funcional con Erlang y Elixir,
     else
     "Sexo desconocido"
     end
     end
     end
    end

### _13. Case_
    defmodule Persona3 do
     def sexo(sex) do
     case sex do
     :m -> "Masculino"
     :f -> "Femenino"
     _ -> "Sexo desconocido"
     end
     end
    end

### _14. Match Con Funciones_
    #Ejemplo 1
    defmodule Persona4 do
     def sexo(sex) when sex == :m do
     "Masculino"
     end
     def sexo(sex) when sex == :f do
     "Femenino"
     end
     def sexo(_sex) do
     "sexo desconocido"
     end
    end

    #Ejemplo 2
    defmodule Persona5 do
     def sexo(sex) when sex == :m, do: "Masculino"
     def sexo(sex) when sex == :f, do: "Femenino"
     def sexo(_sex), do: "sexo desconocido"
    end

### _15. Cond_
    defmodule Persona6 do
     def sexo(sex) do
     cond do
     sex == :m -> "Masculino"
     sex == :f -> "Femenino"
     true -> "Sexo desconocido"
     end
     end
    end
    ### Herramienta Mix
### _1. Documentación Con ExDoc_
    defp deps do
     [
     {:ex_doc, "~>0.12"}
     ]
     end
### _2. Case_
    defmodule Matematicas do
     def calculadora(opcion,{n1,n2}) do
     case opcion do
     "+" -> n1+n2
     "-" -> n1-n2
     "/" when n2 != 0 -> n1/n2
     "/" when n2 == 0 -> "No se puede dividir por 0"
     "*" -> n1*n2
     _ -> :error
     end
     end
    end
    IO.inspect Matematicas.calculadora("+",{5,4})
    IO.inspect Matematicas.calculadora("-",{5,4})
    IO.inspect Matematicas.calculadora("/",{5,4})
    IO.inspect Matematicas.calculadora("/",{5,0})
    IO.inspect Matematicas.calculadora("*",{5,4})
### _3. Cond_
#### Ejemplo 1
     defmodule DiaSemana do
     def dia(d) do
     cond do
     d == 1 -> "Lunes"
     d == 2 -> "Martes"
     d == 3 -> "Miercoles"
     d == 4 -> "Jueves"
     d == 5 -> "Viernes"
     d == 6 -> "Sabado"
     d == 7 -> "Domingo"
     true -> "Dia no valido"
     end
     end
    end
    IO.puts DiaSemana.dia(1)
    IO.puts DiaSemana.dia(2)
    IO.puts DiaSemana.dia(3)
    IO.puts DiaSemana.dia(4)
    IO.puts DiaSemana.dia(5)
    IO.puts DiaSemana.dia(6)
    IO.puts DiaSemana.dia(7)
    IO.puts DiaSemana.dia(8)
#### Ejemplo 2
    defmodule DiaSemana do
     def dia(d) do
     cond do
     d == "l" or d == "L" -> "Lunes"
     d == "ma" or d == "MA" -> "Martes"
     d == "mi" or d == "MI" -> "Miercoles"
     d == "j" or d == "J" -> "Jueves"
     d == "v" or d == "V" -> "Viernes"
     d == "s" or d == "S" -> "Sabado"
    Fundamentos de programación funcional con Erlang y Elixir,
     d == "d" or d == "D" -> "Domingo"
     true -> "Dia no valido"
     end
     end
    end
    IO.puts DiaSemana.dia("l")
    IO.puts DiaSemana.dia("ma")
    IO.puts DiaSemana.dia("mi")
    IO.puts DiaSemana.dia("j")
    IO.puts DiaSemana.dia("v")
    IO.puts DiaSemana.dia("s")
    IO.puts DiaSemana.dia("d")
    IO.puts DiaSemana.dia("L")
    IO.puts DiaSemana.dia("MA")
    IO.puts DiaSemana.dia("MI")
    IO.puts DiaSemana.dia("J")
    IO.puts DiaSemana.dia("V")
    IO.puts DiaSemana.dia("S")
    IO.puts DiaSemana.dia("D")
    IO.puts DiaSemana.dia("Ma")
    IO.puts DiaSemana.dia("mA")
#### Ejemplo 3
    defmodule DiaSemana do
     def dia(d) do
     d = String.upcase(d)
     cond do
     d == "L" -> "Lunes"
     d == "MA" -> "Martes"
     d == "MI" -> "Miercoles"
     d == "J" -> "Jueves"
     d == "V" -> "Viernes"
     d == "S" -> "Sabado"
     d == "D" -> "Domingo"
     true -> "Dia no valido"
     end
     end
    end
    IO.puts DiaSemana.dia("l")
    IO.puts DiaSemana.dia("ma")
    IO.puts DiaSemana.dia("mi")
    IO.puts DiaSemana.dia("j")
    IO.puts DiaSemana.dia("v")
    IO.puts DiaSemana.dia("s")
    IO.puts DiaSemana.dia("d")
    IO.puts DiaSemana.dia("L")
    IO.puts DiaSemana.dia("MA")
    IO.puts DiaSemana.dia("MI")
    IO.puts DiaSemana.dia("J")
    IO.puts DiaSemana.dia("V")
    IO.puts DiaSemana.dia("S")
    IO.puts DiaSemana.dia("D")
    IO.puts DiaSemana.dia("Ma")
    IO.puts DiaSemana.dia("mA")
### _4. Unless_
    #Ejemplo 1
    defmodule MayorDeEdad do
     def mayor1(edad) do
     unless edad >= 18 do
     "Es menor de edad"
     end
     end
    end

    #Ejemplo 2
    defmodule MayorDeEdad do
     def mayor1(edad) do
     unless edad >= 18 do
     "Es menor de edad"
     end
     end
     def mayor2(edad) do
     if edad < 18 do
     "Es menor de edad"
     end
     end
    end
### _5. Funciones Anónimas_
    #Ejemplo 1
    defmodule Calculadora do
     def suma(n1,n2), do: n1+n2
    end
    suma_anonima = fn(n1,n2) -> n1 + n2 end
    IO.puts(Calculadora.suma(5,4))
    IO.puts(suma_anonima.(5,5))

    #Ejemplo 2
    mayor? = fn(n1,n2) -> if n1 > n2 do true else false end end
    IO.inspect(mayor?.(4,5))
    IO.inspect(mayor?.(5,4))
    IO.inspect(mayor?.(5,5))

    #Ejemplo 3
    mayor? = fn(n1,n2) -> if n1 > n2 do :si else :no end end
    res = mayor?.(4,5)
    IO.puts res
    res = mayor?.(5,4)
    IO.puts res

    #Ejemplo 4
    mayor = fn(n1,n2) ->
     if n1 > n2 do
     {:ok, "#{n1} > #{n2}"}
     else
     {:error, "#{n1} <= #{n2}"}
     end
    end
    IO.inspect mayor.(4,5)
    IO.inspect mayor.(5,4)
    IO.inspect mayor.(5,5)

    #Ejemplo 5
    mayor = fn(n1,n2) ->
     if n1 > n2 do
     {:ok, "#{n1} > #{n2}"}
     else
     {:error, "#{n1} <= #{n2}"}
     end
    end
    {status, res} = mayor.(4,5)
    IO.puts status
    IO.puts res
    {status, res} = mayor.(5,4)
    IO.puts status
    IO.puts res
### _6. Operador Pipe_
    sum = 0
    lista = [1,2,3,4,5]
    lista = tl(lista)
    IO.inspect(lista)
    [num|lista] = lista
    #para sacar el 2
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    #para sacar el 3
    [num|lista] = lista
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    #para sacar el 4
    [num|lista] = lista
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    #para sacar el 5
    [num|lista] = lista
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    IO.puts("EL resultado es: #{sum*sum}")

    #Solucion 1
    defmodule PipeTest do
     def cuadrado(n), do: n*n
     def suma(lista) do
     Enum.sum(lista)
     end
    end
    IO.puts("#{PipeTest.cuadrado(PipeTest.suma(tl([1,2,3,4,5])))}")

    #Solucion 2
    defmodule PipeTest do
     def cuadrado(n), do: n*n
     def suma(lista) do
     Enum.sum(lista)
     end
     def csc(lista) do
     lista
     |> tl
     |> suma
     |> cuadrado
     end
    end
    IO.puts("#{PipeTest.csc([1,2,3,4,5])}")
### _7. Herramientas De Depuración_
    ddefmodule PipeTest do
     def cuadrado(n), do: n*n
     def suma(lista) do
     Enum.sum(lista)
     end
     def csc(lista) do
     lista
     |> tl
     |> IO.inspect
     |> suma
     |> IO.inspect
     |> cuadrado
     end
    end
    IO.puts("#{PipeTest.csc([1,2,3,4,5])}")
### _8. Ciclo For_
    for x <- 1..10 do
     IO.puts(x)
    end

    #Ejemplo 2
    sum = 0
    for x <- 1..10 do
     sum = sum + x
    end
    IO.inspect(sum)

    #Quitando sum para evitar los warnings

    for x <- 1..10 do
     sum = sum + x
    end
    IO.inspect(sum)

    #Asignando el for a la variable sum
    #Eliminando el acumulador dentro del for

    sum = for x <- 1..10 do
     x
    end
    IO.inspect(sum)

    #Al saber que lo que genera es una lista, se puede utilizar la función sum del módulo Enum

    sum = for x <- 1..10 do
     x
    end
    IO.puts Enum.sum(sum)

    #Se puede expresar en una sola línea de código: 

    IO.puts Enum.sum(1..10)
