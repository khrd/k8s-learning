# 1 号機の kube-schedulerを設定し、起動する。

## kube-schedulerの設定

* 設定ファイルは /etc/kubernetes/kube-scheduler.conf です。当ファイルにオプションを追記していき、kube-schedulerを起動してください。
    * `systemctl restart kube-scheduler` で設定反映（プロセス再起動）

* 設定ファイルにてkube-scheduler のbind Address、kube-apiserverのurl指定、kubeconfigの指定をすれば動くはず

* もしかしたら以下のコマンドが必要 (TODO: 原因究明)
```
kubectl taint node $NODENAME node.kubernetes.io/not-ready:NoSchedule-
```

## kube-schedulerの確認

* systemctl status kube-scheduler を複数回実行して、正常に起動していることを確認
* マニフェストをapplyしてPodが動作することを確認
    * 当リポジトリ manifests/05-manifest.yaml を参照
    * pod.spec.nodeName が要らなくなった

