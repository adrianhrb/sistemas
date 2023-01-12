# **ADMINISTRACION LOCAL DE SISTEMAS OPERATIVOS**

## ***Variables - comprimir y empaquetar***:
- El shell dispone de un mecanismo para definir variables que se utilizan para almacenar información usada por los programas del sistema o para uso propio. Algunas variables las usa directamente el propio shell o programas de UNIX.  

- Hay dos tipos de variables, las de entorno y las variables de shell. Las de shell son aquellas locales en una sola "terminal", si abrimos otra no va a estar la variable que hemos definido en la otra shell. En cambio, las variables de entorno se heredan en cualquier otro programa que estemos ejecutando. (Disponibilidad local vs global).

### *Como definir  variables:*
- **Para las variables de entorno se asignan:**
    - $ setenv NOMBRE valor       *#En el shell C*
    - $ NOMBRE = valor; export NOMBRE   *#En los shell de Bourne o Korn*

- **Para las variables de shell:**
    - $ set nombre-valor  *#En el shell C (csh)*
    - $ nombre = valor   *#Shell bourne (bash) o korn (ksh)*

- Como comandos aparte tenemos:
    - $ unset nombre  *Para eliminar la variable*
    - $ set   *Muestra las variables locales y globales*
    - $ env / printenv   *Muestra las variables locales*