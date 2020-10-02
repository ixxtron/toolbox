# TERRAFORM: Useful Commands
```
$ terraform plan			# plan

$ terraform apply			# shortcut for plan & apply - avoid this in production

$ terraform plan -out out.terraform	# terraform plan and write the plan to out file

$ terraform apply out.terraform		# apply terraform plan using out file

$ terraform show			# show current state

$ cat terraform.tfstate			# show state in JSON format
```

```
* terraform console *
> var.myvar
> "${var.myvar}"
---
> var.myvar
hello terraform

### ### MAP #####
> var.mymap
{
  "mykey" = "my value"
}

> var.mymap["mykey"]
my value

> "${var.mymap["mykey"]}"
my value

### ### LISt #####
> var.mylist
[
  1,
  2,
  3,
]
> var.mylist[1]
2

### FUNCTIONS 
> element(var.mylist, 1)
2
> slice(var.mylist, 0, 2)
[
  1,
  2,
]


```

