# Pipeline manual run using Containerlab

1. Build `test-client` image with snappi library to run OTG tests

```Shell
cd DASH/test/test-cases/bmv2_model
docker build -t test-client:local .
```

2. Install Containerlab

```Shell
bash -c "$(curl -sL https://get.containerlab.dev)"
```

3. Prepare the pipeline

```Shell
cd DASH/sirius-pipeline
make p4 sai test
```

4. Deploy the test topology

```Shell
sudo containerlab deploy -t topo.yml
```

5. Configure the appliance by running a SAI test

```Shell
docker exec sirius1 /tests/vnet_out/vnet_out
```

6. Run traffic test

```Shell
docker exec -t test-client bash -c "python3 -m pytest /otg -s"
```

7. Cleanup

```Shell
sudo containerlab destroy -t topo.yml
make clean
```
