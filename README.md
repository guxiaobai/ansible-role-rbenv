# Ansible Role: Rbenv

Installs Rbenv on Ubuntu 20.04

## Requirements

None

## Role Variables


* `rbenv_user`: 系统中必须已经创建该用户。
* `rbenv.rubies`: 配置 Ruby 版本、编译参数，支持多个版本。默认版本为  `2.7.4`
* `rbenv_extra_plugins`:  特殊插件。（非 `root` 用户登录，需要 `acl` 支持)
* `rbenv_extra_dep`: 特殊编译依赖的扩展包

**默认配置**

> 以下变量不推荐覆盖，如有扩展需求应通过上方变量实现。

* `rbenv_build_dep`: 默认编译依赖的扩展包。默认集成 [Suggested build environment](https://github.com/rbenv/ruby-build/wiki#suggested-build-environment) 推荐的扩展包
* `rbenv_basic_plugins`: [`ruby-build`](https://github.com/rbenv/ruby-build)、 [`rbenv-vars`](https://github.com/rbenv/rbenv-vars), [`rbenv-china-mirror`](https://github.com/AndorChen/rbenv-china-mirror)
* `rbenv_version`: 配置 [`rbenv`](https://github.com/rbenv/rbenv) 版本。默认为 `1.2.0` (更多版本号请查看 [rbenv releases page](https://github.com/rbenv/rbenv/releases))


## Dependencies


None

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: guxiaobai.rbenv
      rbenv_user: vagrant
      rbenv_rubies:
        - version: 2.6.8
        - version: 2.7.4
          env:
            RUBY_CONFIGURE_OPTS: --disable-install-doc --enable-shared
      rbenv_extra_dep:
        - acl
        - libjemalloc1
        - libjemalloc-dev
```

## License


BSD

## Ref

* [zzet/rbenv](https://github.com/zzet/rbenv)
