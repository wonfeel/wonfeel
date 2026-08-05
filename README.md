## C++ Developer — многопоточность, GPU-вычисления, графика

![C++](https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![OpenGL](https://img.shields.io/badge/OpenGL-5586A4?style=for-the-badge&logo=opengl&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white)

Пишу на C++. Специализируюсь на параллельных системах и высокопроизводительных вычислениях. Разбираюсь с многопоточностью, CUDA и рендерингом на практике — через собственные проекты, а не по статьям.

Сейчас развиваю движок симуляций: заменяемые CPU/CUDA-бэкенды, разделение симуляции и рендера по потокам, оптимизация вычислительного ядра под память GPU.

**Ищу первую работу — junior C++** (системы, графика, вычисления).
Открыт к Qt / CAD / embedded / gamedev.

---

### Чем занимаюсь

- **Многопоточность** — собственный тред-пул; симуляция и рендер разведены по потокам без гонок; синхронизация через фазовый барьер на атомиках (`Idle → Computing → ReadyToCommit → Committing`), вычисление и коммит гарантированно не пересекаются во времени.
- **GPU / CUDA** — пишу вычислительные ядра, работаю с иерархией памяти (shared memory, тайлинг, экономия обращений к DRAM). Ускорил ядро до **109× относительно CPU**; понимаю, когда GPU реально выигрывает, а когда накладные расходы на запуск ядра съедают весь выигрыш.
- **Графика** — рендерер на OpenGL с нуля: шейдеры, VBO, текстуры, палитры, камера. Пробовал CUDA-GL interop.
- **Архитектура** — разбиваю god-классы на компоненты с одной ответственностью, прячу бэкенды за интерфейсами (`ISimulationBackend`: CPU и CUDA взаимозаменяемы, остальной код не знает, что получил).

---

### Проекты

**[Tessera](https://github.com/wonfeel/Tessera)** — 2D движок симуляций на C++/CUDA/OpenGL
Чанковый мир: симулируются только живые чанки, состояние само расползается в соседние. Симуляция и рендер в отдельных потоках, собственный тред-пул, CUDA-бэкенд с shared-memory тайлингом (до 109× к CPU). Бэкенд симуляции — за одним интерфейсом: один код работает и на CPU, и на GPU без переписывания. ImGui-интерфейс, CI на GitHub Actions.

На движке — три самостоятельные демки, каждая в своём репозитории (подтягивают Tessera через CMake `FetchContent`):

**[HexLife](https://github.com/wonfeel/HexLife)** — игра «Жизнь» Конвея: загрузка `.rle`-паттернов, интерактивное рисование, запись GIF.

<p align="center">
  <img src="https://raw.githubusercontent.com/wonfeel/HexLife/main/assets/gun_eater.gif" height="220" alt="Gosper gun" />
  &nbsp;&nbsp;
  <img src="https://raw.githubusercontent.com/wonfeel/HexLife/main/assets/random_field.gif" height="220" alt="Random field spreading across chunks" />
</p>

**[WaveLight](https://github.com/wonfeel/WaveLight)** — свет как волновое поле на гекс-сетке: хроматическая дисперсия R/G/B, рисуемая призма, направленный луч.

*Дальше в планах — отдельный физический бэкенд за тем же интерфейсом: волновое уравнение (FDTD) и векторные поля.*

**[Wormy](https://github.com/wonfeel/Wormy-c302)** — симуляция тела и нервной системы C. elegans на движке Tessera
Настоящий коннектом из 401 нейрона ([Cook et al. 2019](https://doi.org/10.1038/s41586-019-1352-7)) через разреженный неспайковый интегратор сети управляет физическим телом: активность сети → кривизна мышц → сегментированное тело → resistive-force-theory физика на анизотропном субстрате → положение и ориентация. Никакой скриптованной локомоции — движение целиком следствие нейронной активности.

<p align="center">
  <img src="https://raw.githubusercontent.com/wonfeel/Wormy-c302/main/assets/demo.gif" height="220" alt="C. elegans worm swimming, driven by real connectome" />
  &nbsp;&nbsp;
  <img src="https://raw.githubusercontent.com/wonfeel/Wormy-c302/main/assets/screenshot.png" height="220" alt="Worm simulation screenshot" />
</p>

---

### Навыки

| | |
|---|---|
| **Уверенно** | C++17 · многопоточность · OpenGL · CMake · Git |
| **Базово** | CUDA · GLSL · Python · Linux |
| **Инструменты** | Dear ImGui · GLFW · GLAD · GLM · Ninja · GitHub Actions · MSVC |

---

### Контакты

- **Email** — mishabertyaev@gmail.com
- **Telegram** — [@wanfik](https://t.me/wanfik)
- **Discord** — wonfik
