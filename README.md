# disque-boshrelease
BOSH release for the Disque distributed messaging broker

Quick Usage
---

To deploy, ensuring you are targeting your bosh-lite and have an ubuntu stemcell uploaded:

```
git clone git@github.com:williammartin/disque-boshrelease.git
cd disque-boshrelease
git submodule update --init --recursive
sed -i '' "s/11111111-1111-1111-1111-111111111111/$(bosh status --uuid)/" manifests/disque-lite.yml
bosh deployment manifests/disque-lite.yml
bosh create release --name disque --force && bosh -n upload release && bosh -n deploy
```

You can then connect to your disque server using the disque CLI available from https://github.com/antirez/disque via:

```./disque -h 10.244.3.46 -p 7711```

Full instructions for making the CLI, and commands you can issue are available at the aforementioned disque README
