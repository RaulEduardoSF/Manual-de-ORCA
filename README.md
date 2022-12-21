# ORCA Manual
Introduction to ORCA software that compund some quantum-chemical computational methods cabable of do a geometrical optimization caluculus, Infrared and Ramman spectroscopies, moreover of compute the molecular orbitals and then we be able visulizate trought Avogadro

Introducción al software ORCA que integra metdos computacionales de quimica-cuantica, capaz de realizar calculos de optimización geometrica, calculos de espectroscopía infraroja y de espectroscopía Ramman, ademas de calcular los orbitales moleculares y poder visualizarmos mediante Avogadro.

We use `PBE` functional for approximate the exchange-correlation effect, constrained to Restricted Kohn-Sham equation for closed shell systems and a valence double-zeta basis set with “new” polarization functions `def2-SVP`.

### Geometrical Optimization

The geometrical optimization is declared trought `OPT` instruction.

```ini
! RKS PBE def2-SVP OPT PDBFILE
* xyzfile 0 1 benzeno.xyz 
```

![BenzAv](https://user-images.githubusercontent.com/74220104/208805488-20d3d85d-3a8d-4b47-986d-e56768923529.png)

### Spectroscopy
The `NumFreq` instruction, declare the employing of numerical methods to obtain the Ramman frequencies.

#### IR

```ini
#! RKS PBE def2-SVP 
! PBE def2-SVP
! TightSCF
! NumFreq
* xyz 0 1 benzenoOPT.xyz
```

![benzIR_NIST](https://user-images.githubusercontent.com/74220104/208806107-2ef3d0e2-8889-44f5-b658-89dc080c3444.png)

#### Ramman

```ini
! RKS PBE def2-SVP 
! NumFreq
%ELPROP
   Polar 1
end

* xyzfile 0 1 benzenoOPT.xyz
```
![benzRaman](https://user-images.githubusercontent.com/74220104/208806139-9e603084-7556-4805-9867-47504d268d8f.png)


### Molecular Orbitals

Here is important include the following instructions: `! LargePrint Printbasis PrintMOs`

```ini
#! RKS PBE def2-SVP 
! PBE def2-SVP
! Opt
! LargePrint Printbasis PrintMOs
* xyz 0 1 benzenoOPT.xyz
```

![BenzMOs](https://user-images.githubusercontent.com/74220104/208804185-0ae82b7e-421b-4152-8c49-4986c81ef3e0.png)

All instructions are more detailed in `CalculosOrca.pdf`.

