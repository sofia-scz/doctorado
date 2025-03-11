# Estudio de la interfaz m-ZrO2/H2O y su fisicoquímica desde primeros principios

## Contexto
La acumulación de hidrógeno gaseoso y su potencial como explosivo es un tema de gran interés en el ámbito de la seguridad nuclear (Sherman, 1984). En los tres grandes accidentes en la historia de la energía nuclear; Fukushima, Three Mile Island y Chernobyl; se cree que la combustión de hidrógeno producido en el interior del reactor jugó un rol clave en el desarrollo del accidente (Sherman, 1984; Sahin & Sarwar, 2013; Yanez et al, 2015).

Para abordar este problema, nos interesa partir del estudio de los mecanismos involucrados en la generación del hidrógeno gaseoso. Sherman mencionas varios mecanismos posibles, que distinge entre rápidos y lentos, siendo los rápidos los más relevantes en caso de accidente. Específicamente nos vamos a centrar en uno de estos, que es la reacción entre el zirconio de los claddings del combustible y el agua. En esta reacción, a escala global, se produce la oxidación de zirconio metálico que toma el oxígeno del agua, y la reducción del hidrógeno que se libera como gas (Urbanic & Heidrick, 1978). Según Sherman, esta reacción es la fuente de hidrógeno más importante en un accidente. Sin embargo, no existe en la literatura un marco teórico riguroso para muchos de estos mecanismos, aunque existen una gran cantidad de mediciones experimentales (IAEA, 2011). Con esto en mente, nos proponemos a estudiar estos fenómenos con expectativas de describirlos desde primeros principios.

## Metodología
Nuestra metodología es fundamentalmente teórica y computacional, y nos vamos a apoyar en dos tipos de cálculos: dinámica molecular para determinar propiedades térmicas y cinécticas, y DFT para el cálculo de propiedades electrónicas y para el sampleo de la PES del sistema. A su vez, emplearemos métodos de machine learning al construir potenciales de interacción para las MDs entrenados para imitar la PES calculada por DFT.



## Referencias
- Sherman, M. P. (1984). Hydrogen combustion in nuclear plant accidents and associated containment loads. Nucl. Eng. Des., 82(1), 13–24. doi: 10.1016/0029-5493(84)90263-2
- Şahin, S., & Sarwar, M. S. (2013). Hydrogen hazard and mitigation analysis in PWR containment. Ann. Nucl. Energy, 58, 132–140. doi: 10.1016/j.anucene.2013.03.001
- Yanez, J., Kuznetsov, M., & Souto-Iglesias, A. (2015). An analysis of the hydrogen explosion in the Fukushima-Daiichi accident. International Journal of Hydrogen Energy, 40(25), 8261–8280. doi:10.1016/j.ijhydene.2015.03.154
- Urbanic, V. F., & Heidrick, T. R. (1978). High-temperature oxidation of zircaloy-2 and zircaloy-4 in steam. Journal of Nuclear Materials, 75(2), 251–261. doi:10.1016/0022-3115(78)90006-5
- INTERNATIONAL ATOMIC ENERGY AGENCY (2011). Mitigation of Hydrogen Hazards in Severe Accidents in Nuclear Power Plants, IAEA-TECDOC-1661.
