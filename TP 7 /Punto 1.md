## Errores en bits de Filas y Columnas

Si cambian dos bits situados en filas distintas (Fi, Fj) y columnas distintas (Ck, Cm), las paridades calculadas fallaran en dos filas y en dos columnas. Si esto pasara el código detectaría la existencia de un error, y al utilizar el método de paridad bidimensional para corregir los errores, se esta en una situación de ambigüedad. Esto ocurre porque existen dos combinaciones posibles de intersección que producen exactamente las mismas fallas de paridad: las posiciones (Fi, Ck) y (Fj, Cm), las posiciones (Fi, Cm) y (Fj, Ck). Esto hace que el método no pueda determinar que pares de bits fueron los alterados, ósea, perdemos toda capacidad de corrección automática.

