# elogin #

A minimal demonstration of EAuth login in Urbit

## Build/Develop ##

All commands assume that the current working directory is this repository's
base directory and use [durploy] to streamline various Urbit development
workflows.

### Generate Full Desk ###

```bash
cd ./desk
rm -rI full/
find bare -type f | while read f; do { d=$(dirname "$f" | sed "s/^bare/full/"); mkdir -p "$d"; ln -sr -t "$d" "$f"; }; done
mkdir -p full/lib/ full/mar full/sur
ln -sr ../LICENSE.txt full/license.txt
git clone --depth 1 https://github.com/urbit/yard yar
cp yar/desk/lib/{dbug*,default-agent*,skeleton*,schooner*,server*,docket*} full/lib/
cp yar/desk/mar/{bill*,docket*,hoon*,json*,kelvin*,mime*,noun*,ship*,txt*} full/mar/
cp yar/desk/sur/docket* full/sur/
```

### Deploy Full Desk ###

```bash
./durploy desk -w zod elogin ./desk/full/
```


[urbit]: https://urbit.org
[durploy]: https://github.com/sidnym-ladrut/durploy

[fakezod]: https://developers.urbit.org/guides/core/environment#development-ships
[react]: https://reactjs.org/
[tailwind css]: https://tailwindcss.com/
[vite]: https://vitejs.dev/
