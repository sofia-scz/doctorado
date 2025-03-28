# Estudio de la interfaz m-ZrO2/H2O y su fisicoquímica desde primeros principios

## Contexto
La acumulación de hidrógeno gaseoso y su potencial como explosivo es un tema de gran interés en el ámbito de la seguridad nuclear (Sherman, 1984). En los tres grandes accidentes en la historia de la energía nuclear; Fukushima, Three Mile Island y Chernobyl; se cree que la combustión de hidrógeno producido en el interior del reactor jugó un rol clave en el desarrollo del accidente (Sherman, 1984; Sahin & Sarwar, 2013; Yanez et al, 2015).

Para abordar este problema, nos interesa partir del estudio de los mecanismos involucrados en la generación del hidrógeno gaseoso. Sherman mencionas varios mecanismos posibles, que distinge entre rápidos y lentos, siendo los rápidos los más relevantes en caso de accidente. Específicamente nos vamos a centrar en uno de estos, que es la reacción entre el zirconio de los claddings del combustible y el agua. En esta reacción, a escala global, se produce la oxidación de zirconio metálico que toma el oxígeno del agua, y la reducción del hidrógeno que se libera como gas (Urbanic & Heidrick, 1978). Según Sherman, esta reacción es la fuente de hidrógeno más importante en un accidente. Sin embargo, no existe en la literatura un marco teórico riguroso para muchos de estos mecanismos, aunque existen una gran cantidad de mediciones experimentales (IAEA, 2011). Con esto en mente, nos proponemos a estudiar estos fenómenos con expectativas de describirlos desde primeros principios.

## Metodología
Nuestra metodología es fundamentalmente teórica y computacional, y nos vamos a apoyar en dos tipos de cálculos: dinámica molecular para determinar propiedades térmicas y cinécticas, y DFT para el cálculo de propiedades electrónicas y para el sampleo de la PES del sistema. A su vez, emplearemos métodos de machine learning al construir potenciales de interacción para las MDs entrenados para imitar la PES calculada por DFT.

### Funcional de XC y pseudopotenciales para DFT
El funcional más común empleado en DFT es el funcional PBE, sin embargo tiene serias limitaciones para modelar agua, que está presente en nuestro sistema. Por esto optamos por un funcional relativamente moderno que pertenece al grupo de los funcionales meta-GGA (es decir, incorporan la energía cinética de los electrones por sobre la aproximación de GGA), que es el funcional SCAN. En recientes estudios se vió que mejora notablemente la descripción del agua por sobre otros funcionales de DFT (Zhang et al, 2021). Más aún, benchmarks sobre grandes bases de datos han confirmado que SCAN supera a los funcionales de GGA en aspectos como la predicción de energías de cohesión, geometrías y termoquímica para diversos sistemas como sólidos, clusters moleculares, entre otros (Sun et al, 2016; Kingsbury et al, 2022).

Se ha señalado que al trabajar con códigos de ondas planas y pseudopotenciales, es conveniente o en algunos casos necesario, emplear pseudopotenciales generados con el mismo funcional de DFT que se emplea en el cálculo de ondas planas, en particular para el funcional SCAN (Yao & Kanai, 2017). Empleamos en nuestros cálculos los pseudopotenciales de H y O publicados por Yao, sin embargo los autores no han publicado uno para el zirconio, por lo que construimos el propio con el método y el programa de los autores, quienes nos han cedido su programa amablemente. 

En la próxima tabla mostramos los resultados para varios pseudopotenciales que generamos para SCAN, con distintos radios de pseudización y configuración electrónica de referencia, y los resultados de su testeo para h-Zr metálico y m-ZrO2. Además, comparamos con cálculos de referencia que incluyen el cálculo con pseudopotenciales de PBE, el cálculo all electron con PBE y la medición experimental a baja temperatura (4K). 

| | Zr+2 - soft |  Zr+2 - hard | Zr* - soft | Zr* - hard | PseudoDojo (PBE) | Wien2k (PBE) | Exp |
| - | --- | --- | --- | --- | --- | --- | --- |
| Pseudo Conf Ele Ref | [Kr] 4d2 5s0 | [Kr] 4d2 5s0 | [Kr] 4d4 5s0 | [Kr] 4d4 5s0 | [Kr] 4d3 5s1 |  All electron | |
| Densidad h-Zr | 6.503 | 6.504 | 6.486 | 6.507 | 6.45 | 6.48 | 6.52 |
| Densidad m-ZrO2 | 5.775 | 5.777 | 5.762 | 5.776 |   |   | 5.78 |


## Referencias
- Sherman, M. P. (1984). Hydrogen combustion in nuclear plant accidents and associated containment loads. Nucl. Eng. Des., 82(1), 13–24. doi: 10.1016/0029-5493(84)90263-2
- Şahin, S., & Sarwar, M. S. (2013). Hydrogen hazard and mitigation analysis in PWR containment. Ann. Nucl. Energy, 58, 132–140. doi: 10.1016/j.anucene.2013.03.001
- Yanez, J., Kuznetsov, M., & Souto-Iglesias, A. (2015). An analysis of the hydrogen explosion in the Fukushima-Daiichi accident. International Journal of Hydrogen Energy, 40(25), 8261–8280. doi:10.1016/j.ijhydene.2015.03.154
- Urbanic, V. F., & Heidrick, T. R. (1978). High-temperature oxidation of zircaloy-2 and zircaloy-4 in steam. Journal of Nuclear Materials, 75(2), 251–261. doi:10.1016/0022-3115(78)90006-5
- INTERNATIONAL ATOMIC ENERGY AGENCY (2011). Mitigation of Hydrogen Hazards in Severe Accidents in Nuclear Power Plants, IAEA-TECDOC-1661.
- Zhang, L., Wang, H., Car, R., & E, W. (2021). Phase Diagram of a Deep Potential Water Model. Physical Review Letters, 126(23). doi:10.1103/physrevlett.126.236001
- Kingsbury, R., Gupta, A. S., Bartel, C. J., Munro, J. M., Dwaraknath, S., Horton, M., & Persson, K. A. (2022). Performance comparison of r2SCAN and SCAN metaGGA density functionals for solid materials via an automated, high-throughput computational workflow. Phys. Rev. Mater., 6(1), 013801. doi: 10.1103/PhysRevMaterials.6.013801
- Sun, J., Remsing, R. C., Zhang, Y., Sun, Z., Ruzsinszky, A., Peng, H., ...Perdew, J. P. (2016). Accurate first-principles structures and energies of diversely bonded systems from an efficient density functional. Nat. Chem., 27554409. Retrieved from https://pubmed.ncbi.nlm.nih.gov/27554409
- Yao, Y., & Kanai, Y. (2017). Plane-wave pseudopotential implementation and performance of SCAN meta-GGA exchange-correlation functional for extended systems. J. Chem. Phys., 146(22). doi: 10.1063/1.4984939
