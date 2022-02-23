# Makefile 應用經驗分享簡報

---

這是一個 #Build 的工具

<br>

```bash
make foo.txt
```

---

### Makefile 簡單的格式

```makefile
foo.txt
	echo "foo" > foo.txt

bar.txt
	echo "bar" > bar.txt
```

---

### 應用實例

```makefile
build:  
	docker build -t=seagon .  

shell:  
	docker run --rm -it -p 8000:8000 seagon bash  

run:  
	docker run --rm -it -p 8000:8000 seagon
```

---

### 試試看？

```bash
touch build
make build
```

---

### PHONY 用法 1

```makefile
.PHONY: build

build:  
	docker build -t=seagon .  

```

---

### PHONY 用法 2

```makefile
SLEEP = 1 2 3 4 5

go:
	@for dir in $(SLEEP); do \
		echo $$dir; \
	done
```

---

### PHONY 用法 2 - 續

```makefile
SLEEP = 1 2 3 4 5

.PHONY: go $(SLEEP)

go: $(SLEEP)

$(SLEEP):
	@sleep $@ && echo $@
```

* [參考資料](https://www.gnu.org/software/make/manual/html_node/Phony-Targets.html)