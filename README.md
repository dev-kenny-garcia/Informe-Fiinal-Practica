# Informe Final de Practica Profesional

Proyecto LaTeX para generar el informe final de practica profesional.

## Requisitos

- MiKTeX, TeX Live o una distribucion LaTeX compatible.
- `xelatex`, porque el proyecto usa `fontspec` y fuentes locales.
- `makeglossaries`, necesario para generar el glosario de acronimos.

## Estructura

- `main.tex`: archivo principal del informe.
- `chapters/`: capitulos y paginas de contenido.
- `config/packages.tex`: paquetes LaTeX.
- `config/commands.tex`: comandos y estilos personalizados.
- `config/acronyms.tex`: definicion de acronimos.
- `config/front_page.tex`: portada.
- `images/`: imagenes usadas por la plantilla.

## Compilar el PDF

Ejecuta estos comandos desde la raiz del proyecto:

```powershell
xelatex main.tex
makeglossaries main
xelatex main.tex
xelatex main.tex
```

El PDF final se genera como `main.pdf`.

## Usar acronimos

Los acronimos se definen en `config/acronyms.tex` con `\newacronym`:

```tex
\newacronym{its}{ITS}{Sistemas de Transporte Inteligente, Intelligent Transportation System}
```

La estructura es:

```tex
\newacronym{clave}{SIGLA}{Nombre completo}
```

Luego se usan en los capitulos con:

```tex
\gls{its}
```

La primera vez que se use, LaTeX muestra el nombre completo y la sigla. Las siguientes veces muestra solo la sigla.

Para registrar un acronimo en el glosario sin imprimir texto en esa posicion, usa:

```tex
\glsadd{qa}
```

## Glosario de acronimos

El glosario se imprime en `main.tex` con:

```tex
\printglossary[
    type=\acronymtype,
    title={Glosario de Acr\'onimos},
    style=acronymtab
]
```

El estilo visual del glosario esta definido en `config/commands.tex` como `acronymtab`.

## Numeracion

Las paginas preliminares usan numeracion romana. Despues del glosario, `main.tex` cambia a numeracion arabiga para que el capitulo 1 inicie en la pagina `1`.
