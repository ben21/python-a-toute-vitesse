# Installation

Dans ce chapitre nous installerons et lancerons l'interpréteur Python sur votre ordinateur.

## Pour installer sur Windows

1.  Téléchargez la dernière version de Python 3 pour Windows à <https://www.python.org/downloads/windows/> et lancez l'installeur. Au moment d'écrire ce livre, la dernière version est Python 3.7.4.

2.  Assurez-vous de sélectionner les paramètres "Install launcher for all users" et "Add Python to PATH", et choisissez "Customize installation".

    ![Windows installation](images/python_windows.jpg){width=62%}

3.  Sur l'écran suivant, "Optional Features", vous pouvez tout installer, mais il est surtout essentiel d'installer "pip" et "pylauncher (for all users)". Pip est le gestionnaire de paquets de Python qui vous permet d'installer de nombreux paquets et bibliothèques.

4.  Dans les Options Avancées, assurez-vous de sélectionner "Add Python to environment variables". Aussi, je vous suggère de changer l'emplacement de l'installation vers quelque chose comme C:\\Python36\\. Ce sera plus facile pour vous de retrouver l'installation de Python en cas de problème.

    ![Windows installation](images/python_windows2.jpg){width=62%}

5.  Finalement, permettez à Python d'utiliser plus de 260 charactères dans le système de fichiers en sélectionnant "Disable path length limit" et fermez la boite de dialogue d'installation

    ![Windows installation](images/python_windows3.jpg){width=62%}

6.  Maintenant, ouvrez la ligne de commande (cmd) et exécutez "python" ou "python3". Si tout est correctement installé, vous devriez voir la REPL de Python. La REPL (pour Read, Evaluate, Print Loop) est un environnement que vous pouvez utiliser pour programmer des petits bouts de code en Python. Tapez *exit()* pour quitter la REPL.

    ![Python REPL](images/python_windows4.jpg){width=62%}

## Pour installer sur MacOS

Vous pouvez télécharger les derniers exécutables depuis <https://www.python.org/downloads/mac-osx/>. Assurez-vous de télécharger les dernières versions pour Python 3 (Python 3.7.4 au moment d'écrire ces lignes).Vous pouvez également utiliser Homebrew, un gestionnaire de paquets pour MacOS (<https://brew.sh/>). Pour installer la dernière version de Python 3 avec Homebrew, tapez "`brew install python3`" sur votre terminal. Une autre option est d'utiliser le gestionnaire de paquets MacPorts (<https://www.macports.org/>) et la commande "`port install python36`".

![Python REPL](images/python_macos.png){width=62%}

Finalement, ouvrez le terminal, exécutez `python3` et vous devriez voir la REPL de Python comme expliqué plus haut. Pressez Ctrl+D ou tapez `exit()` pour quitter la REPL.

## Pour installer sur Linux

Pour installer Python sur Linux, vous pouvez télécharger les derniers fichiers sources de Python 3 depuis <https://www.python.org/downloads/source/> ou utiliser le gestionnaire de paquets (apt-get, aptitude, synaptic ou autres) pour l'installer. Pour vous assurer d'avoir Python 3 installé sur votre système, tapez `python3 --version` dans votre terminal.

Finalement, ouvrez le terminal, exécutez `python3` et vous devriez voir la REPL de Python comme dans l'image suivante. Pressez Ctrl+D ou tapez `exit()` pour quitter la REPL.

![Python REPL](images/python_linux.png){width=62%}
