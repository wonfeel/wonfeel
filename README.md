## C++ Developer — многопоточность, GPU-вычисления, графика

![C++](https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![OpenGL](https://img.shields.io/badge/OpenGL-5586A4?style=for-the-badge&logo=opengl&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white)

Пишу на C++. Специализируюсь на параллельных системах и высокопроизводительных вычислениях. Разбираюсь с многопоточностью, CUDA и рендерингом на практике — через собственные проекты, а не по статьям.

Сейчас развиваю движок симуляций: заменяемые CPU/CUDA-бэкенды, разделение симуляции и рендера по потокам, оптимизация вычислительного ядра под память GPU.

---

### Чем занимаюсь

- **Многопоточность** — собственный тред-пул; симуляция и рендер разведены по потокам без гонок; синхронизация через фазовый барьер на атомиках (`Idle → Computing → ReadyToCommit → Committing`), вычисление и коммит гарантированно не пересекаются во времени.
- **GPU / CUDA** — пишу вычислительные ядра, работаю с иерархией памяти (shared memory, тайлинг, экономия обращений к DRAM). Ускорил ядро до **109× относительно CPU**; понимаю, когда GPU реально выигрывает, а когда накладные расходы на запуск ядра съедают весь выигрыш.
- **Графика** — рендерер на OpenGL с нуля: шейдеры, VBO, текстуры, палитры, камера. Пробовал CUDA-GL interop.
- **Архитектура** — разбиваю god-классы на компоненты с одной ответственностью, прячу бэкенды за интерфейсами (`ISimulationBackend`: CPU и CUDA взаимозаменяемы, остальной код не знает, что получил).

---

### Проекты

**[Tessera](https://github.com/wonfeel/Tessera)** — 2D движок клеточных автоматов на C++/CUDA/OpenGL
Чанковый мир: симулируются только живые чанки, жизнь сама расползается в соседние. Симуляция и рендер в отдельных потоках, собственный тред-пул, CUDA-бэкенд с shared-memory тайлингом (до 109× к CPU). Правило автомата — таблица подстановки: один код работает и на CPU, и на GPU без переписывания. Загружает `.rle`-паттерны, пишет GIF, ImGui-интерфейс, CI на GitHub Actions.

<p align="center">
  <img src="https://raw.githubusercontent.com/wonfeel/Tessera/main/assets/gun_eater.gif" height="220" alt="Gosper gun" />
  &nbsp;&nbsp;
  <img src="https://raw.githubusercontent.com/wonfeel/Tessera/main/assets/random_field.gif" height="220" alt="Random field spreading across chunks" />
</p>

*Дальше в планах — отдельный физический бэкенд за тем же интерфейсом: волновое уравнение (FDTD) и векторные поля.*

---

### Стек

| | |
|---|---|
| **Языки** | C++17 (основной) · Python · CUDA C++ |
| **Графика / GPU** | OpenGL · GLSL · CUDA · GLFW · GLAD · GLM · Dear ImGui |
| **Инструменты** | CMake · Ninja · Git · GitHub Actions · MSVC |

---

### Контакты

- **Email** — mishabertyaev@gmail.com
- **Telegram** — [@wanfik](https://t.me/wanfik)
- **Discord** — wonfik

---

<div align="center">
<img src="https://github-readme-stats.vercel.app/api?username=wonfeel&show_icons=true&hide_border=true&count_private=true" alt="GitHub stats" />
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=wonfeel&layout=compact&hide_border=true" alt="Top languages" />
</div>
