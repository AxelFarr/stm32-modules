# stm32-modules
Objectif de ce projet : mettre à disposition une série de modules pour des capteurs ou composants électroniques basiques, afin de faciliter leur intégration dans des projets.

## Routine de lancement d'un projet sur STM32 cube IDE
1 - Choisir la carte utilisée.  
2 - Le choix de l'option "Enable defaut PIN" dépend de la carte utilisée. Sur des cartes simples, il peut être intéressant d'accepter. Cependant sur des cartes comme la STM32F7, plus complexe, il est plus simple de refuser et de ne choisir que les PIN qui nous intéressent pour un projet donné.  
3 - Une fois le projet créé, dans l'interface ".ioc", on peut effectuer un "Pinout/clear pinout" en fonction de l'étape précédente.  
4 - Dans "System Core/SYS", s'assurer que "Debug" est en mode "Serial wire", pour permettre la communication série entre l'ordinateur et la carte.   
5 - Pour que cette dernière soit effective, il faut également activer une liaison UART (cette dernière change en fonction de la carte utilisée). Sur la stm32F746G, il s'agit de l'USART1 à mettre sur les PINs PB7 et PA9 (/!\ ce ne sont pas toujours les PINs activés par défaut !).  
6 - Activer l'horloge (je prends toujours l'horloge externe HSE) dans "System Core/ RCC" (il faut mettre HSE sur "Crystal/Ceramic Resonator"). Pour que l'horloge soit active, il faut ensuite se rendre dans "Clock Configuration", cocher HSE au niveau du MUX et changer HCLK à sa valeur max.  
7 - Enfin, dans le "project manager", dans l'onglet "code generator", cocher l'option "Generate peripheral initialization as a paur of...". Ceci va permettre de répartir de code de configuration dans des fichiers spécifique et de ne pas tout mettre dans le main (parce que sinon c'est moche). Et voilà !
