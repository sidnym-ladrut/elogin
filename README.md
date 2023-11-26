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
mkdir -p full/lib/
ln -sr ../LICENSE.txt full/license.txt
git clone -b 412k-rc2 --depth 1 https://github.com/urbit/urbit.git urb
cp urb/pkg/arvo/mar/{bill*,hoon*,json*,kelvin*,mime*,noun*,ship*,txt*} full/mar/
cp urb/pkg/arvo/lib/{agentio*,dbug*,default-agent*,skeleton*} full/lib/
git clone -b v1.16.0 --depth 1 https://github.com/tloncorp/landscape.git lan
cp lan/desk/mar/docket* full/mar/
cp lan/desk/lib/docket* full/lib/
cp lan/desk/sur/docket* full/sur/
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
