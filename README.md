
# AsciiArtify | аналіз: minikube, kind та k3d

# 👋 Вступ

[Kubernetes](https://kubernetes.io/) є одним з найпопулярніших інструментів для розгортання та керування контейнерами. У цьому документі розглядаються три інструменти на базі Kubernetes для розгортання та тестування кластерів в локальному середовищі: [minikube](https://minikube.sigs.k8s.io/docs/), [kind](https://kind.sigs.k8s.io/) та [k3d.](https://k3d.io/v5.4.9/) Для забезпечення безпеки та контролю над процесом розробки **AsciiArtify** використовуватиме GitHub як систему контролю версій.

## **📝 Характеристики:**

| ХАРАКТЕРИСТИКИ       | Minikube                                                                                                                                                                 | Kind                                                                                                                                                                | K3d                                                                                                                                                                                   |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ОС                   | Linux🐧, MacOs🍎, Windows🖥️                                                                                                                                                 | Linux🐧, MacOs🍎, Windows🖥️                                                                                                                                            | Linux🐧, MacOs🍎,                                                                                                                                                                       |
| АРХІТЕКТУРИ          | amd64 / x86_64 arm64 / AArch64 arm / AArch32 (32-біт) ppc64le, s390x                                                                                                     | x86_64,amd64, arm64                                                                                                                                                 | x86_64/amd64, aarch64/arm64 arm64                                                                                                                                                     |
| АВТОМАТИЗАЦІЯ        | ✅                                                                                                                                                                        | ✅                                                                                                                                                                   | ✅                                                                                                                                                                                     |
| СПОСІБ АВТОМАТИЗАЦІЇ | автоматизація через: shell скрипти або Terraform                                                                                                                         | автоматизація через:використовуючи Kubernetes API або YAML файл.                                                                                                    | автоматизація через:використовуючи shell скрипти або Docker Compose.                                                                                                                  |
| ДОДАТКОВІ ФУНКЦІЇ    | Наявність додаткових функцій: підтримка Docker, CRI-O та containerd; встановлення Add-ons, таких як Kubernetes Dashboard, Ingress Controller та Heapster для моніторингу | можливість використання будь-якого образу Docker; встановлення Add-ons, таких як Kubernetes Dashboard, Ingress Controller та моніторингу.                           | підтримка Docker Compose для конфігурування кластера; можливість використання будь-якого образу Docker; підтримка моніторингу та керування Kubernetes кластером за допомогою Rancher. |
| ПЕРЕВАГИ             | Підтримка різноманітності архітектур та ОС. Автоматизація за допомогою shell скриптів або Terraform- Наявність різноманітних Add-ons для моніторингу та керування        | Дуже простий у використанні та має мінімальні вимоги до ресурсів- Підтримка різноманітності архітектур та режимів роботи Kubernetes- Гнучкі можливості налаштування | Підтримка Docker Compose для конфігурування кластера. Можливість використання будь-якого образу Docker. Підтримка моніторингу та керування Kubernetes кластером за допомогою Rancher  |

## **🤔 Переваги та недоліки**

|       💻 Інструмент         |➕ ПЕРЕВАГИ                          |➖ НЕДОЛІКИ                         |
|----------------|-------------------------------|-----------------------------|
|**[Minikube](https://minikube.sigs.k8s.io/docs/start/)**|`○ Легко встановлюється і використовується для локального тестування Kubernetes. Має велику кількість документації та підтримки спільноти. Швидкість розгортання відносно низька через використання віртуальних машин.Надає можливість налаштовувати різні параметри Kubernetes кластера, наприклад, кількість вузлів та ресурсів, які вони використовують.`            |`○ Minikube може бути повільним при запуску та вимагати більше ресурсів порівняно з Kind або K3d,Може бути нестабільним на деяких операційних системах, особливо на Windows. Не підтримує різноманітність архітектур та режимів роботи Kubernetes. Вимагає великої кількості ресурсів (RAM, CPU) для більш складних додатків`           |
|**[Kind](https://kind.sigs.k8s.io/)**         |`○ Дуже простий у використанні та має мінімальні вимоги до ресурсів. Підтримує різноманітність архітектур та режимів роботи Kubernetes. Має гнучкі можливості налаштування.`        |`○ Немає готових графічних інтерфейсів користувача, тому вимагає деякої ручної роботи для налаштування та використання. Швидкість розгортання може бути повільною у випадку великих додатків або при запуску багатьох екземплярів. Kind не підтримує ряд додаткових функцій, таких як Network Policies та StatefulSets, і може потребувати деяких налаштувань для використання з іншими інструментами.`
|**[K3d](https://k3d.io/v5.4.9/)**          |`○ K3d має дуже простий інтерфейс, що робить його легким у використанні. K3d вимагає мінімальної кількості ресурсів (RAM, CPU), що робить його ідеальним вибором для локального тестування. K3d підтримує різні архітектури та режими роботи Kubernetes, що робить його універсальним інструментом для тестування. Можливість автоматичної настройки Kubernetes кластера за допомогою Docker Compose, що дозволяє запускати багато вузлів та налаштовувати їх ресурси зручним для вас способом.`|`○ K3d може мати обмеження в масштабованості та ефективності при запуску багатьох вузлів, а також може бути складніше налаштувати мережу для кластера.K3d може мати проблеми зі сумісністю з деякими іншими інструментами або додатками, а також може потребувати деяких додаткових настройок для роботи з вузлами, які запущені на різних машинах`|

## **🎥 Демонстрація**

![Image](.demo/demo_AsciiArtify.gif)

<iframe width="560" height="315" src="https://www.youtube.com/embed/EyYHtBU_mEk" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>



## **🚨 Висновки**

Заключення та рекомендації щодо використання кожного інструменту в PoC для стартапу

> Minikube є дуже популярним інструментом, який має велику кількість документації та підтримки спільноти. Він легко встановлюється та використовується для локального тестування Kubernetes, але може бути нестабільним на деяких операційних системах та вимагає великої кількості ресурсів для більш складних додатків.

>Kind є дуже простим у використанні та має мінімальні вимоги до ресурсів. Він підтримує різноманітність архітектур та режимів роботи Kubernetes та має гнучкі можливості налаштування. Однак, він не має готових графічних інтерфейсів користувача та швидкість розгортання може бути повільною у випадку великих додатків або запуску багатьох екземплярів.

>K3d також є дуже простим у використанні та має мінімальні вимоги до ресурсів. Він підтримує різноманітність архітектур та режимів роботи Kubernetes та має готовий веб-інтерфейс користувача. Однак, він може бути нестабільним у випадку розгортання більш складних додатків.

>

 В залежності від конкретних потреб вашого проекту, будь-який з трьох варіантів (Minikube, Kind або K3d) може бути хорошим вибором для системи локальної розробки. Однак, я рекомендую використовувати **K3d** з таких причин:
🚀

- *K3d має значно менше вимог до ресурсів порівняно з Minikube або Kind, що дозволяє запускати більш потужні кластери на менш потужних комп'ютерах.*
- *K3d підтримує більше функцій, включаючи Network Policies та StatefulSets, порівняно з Kind, а також може працювати з більшою кількістю вузлів та розгалужених кластерів, порівняно з Minikube.*
- *K3d може бути легшим у використанні та швидким у налаштуванні порівняно з іншими інструментами, що дозволяє швидко почати розробку та тестування.*

Отже, якщо ви шукаєте легкий, швидкий і простий у використанні інструмент для локальної розробки та тестування, K3d може бути відмінним варіантом для вашого проекту.
