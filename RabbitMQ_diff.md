## list Qs
```bash
curl -u rabbit-stg:TndoANLjVmgFyoDMRmVzulGdLjSD66md https://rabbib-host/api/queues  | jq '.[].name' | grep SMHT
```

## delete Qs  contens

```bash
while read p; do

  q=$(echo $p | tr -d '"')
    echo $q
  curl -XDELETE -u rabbit-stg:TndoANLjVmgFyoDMRmVzulGdLjSD66md http://rabbitmq-proxy/api/queues/%2f/$q/contents
done <all.q
```
## Delete Q completely
```bash
while read p; do
  q=$(echo $p | tr -d '"')
    echo $q
  curl -i -XDELETE -u rabbit-stg:TndoANLjVmgFyoDMRmVzulGdLjSD66md https://<rabbitmq-proxy>/api/queues/%2f/$q
done <t3
bash
