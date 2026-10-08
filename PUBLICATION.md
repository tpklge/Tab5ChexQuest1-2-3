# Compilação do port Chex 1/2/3

O port jogável está em research/idf, baseado em ZDoom 2.8.1. A aplicação
ESP-IDF da raiz mantém a referência histórica Freedoom e não é o port Chex.
Ative ESP-IDF 5.4.4, instale CMake e um compilador C/C++ nativo, então:

```sh
git clone --depth 1 --branch 2.8.1 https://github.com/rheit/zdoom.git research/zdoom-2.8.1
git -C research/zdoom-2.8.1 apply ../probe/zdoom-rv32-types.patch
python3 tools/prepare_zdoom.py
idf.py -C research/idf set-target esp32p4
idf.py -C research/idf build
```

No Mac usado durante o desenvolvimento, a geração nativa exigiu
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk.

Instale research/idf/build/Tab5CHEX_ZDoomExperimental.bin pelo M5Launcher.
Copie research/generated/zdoom.pk3 para /doom no microSD. Forneça separadamente
chex.wad (Chex 1), chex.wad + chex2.wad (Chex 2), chex3.wad original v1.4
(Chex 3). Não usar a edição v2/GZD como substituta. O menu mostra apenas os
jogos disponíveis. Saída reinicia para o seletor; configs/saves são separados.
Efeitos ES8388 habilitados; música desativada.

Nenhum WAD, clone ZDoom ou firmware pré-compilado acompanha o repositório.
Leia README.md, research/idf/README.md e THIRD_PARTY_NOTICES.md.
