# rbs_validate_with_nonreturn_void_bug

This repository is a minimal reproduction of a bug of `rbs validate`.

## Steps to reproduce

1. Clone
2. Run `bundle install`
3. Run `bundle exec rbs -Isig validate`

You'll see an error like this:

```
$ bundle exec rbs -Isig validate
bundler: failed to load command: rbs (/Users/tkomiya/.rbenv/versions/3.3.2/bin/rbs)
/Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/method_type.rb:134:in `with_nonreturn_void?': undefined method `with_nonreturn_void?' for an instance of RBS::Types::UntypedFunction (NoMethodError)

          block.type.with_nonreturn_void? || block.self_type&.with_nonreturn_void? || false
                    ^^^^^^^^^^^^^^^^^^^^^
Did you mean?  with_nonreturn_void
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:274:in `void_type_context_validator'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:155:in `block (4 levels) in validate_class_module_definition'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:154:in `each'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:154:in `block (3 levels) in validate_class_module_definition'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/ast/declarations.rb:14:in `block in each_member'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/ast/declarations.rb:12:in `each'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/ast/declarations.rb:12:in `each_member'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:150:in `block (2 levels) in validate_class_module_definition'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:149:in `each'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:149:in `block in validate_class_module_definition'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:97:in `each'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:97:in `validate_class_module_definition'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli/validate.rb:84:in `run'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli.rb:447:in `run_validate'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/lib/rbs/cli.rb:140:in `run'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/rbs-3.5.1/exe/rbs:7:in `<top (required)>'
	from /Users/tkomiya/.rbenv/versions/3.3.2/bin/rbs:25:in `load'
	from /Users/tkomiya/.rbenv/versions/3.3.2/bin/rbs:25:in `<top (required)>'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/cli/exec.rb:58:in `load'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/cli/exec.rb:58:in `kernel_load'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/cli/exec.rb:23:in `run'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/cli.rb:451:in `exec'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/vendor/thor/lib/thor/command.rb:28:in `run'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/vendor/thor/lib/thor/invocation.rb:127:in `invoke_command'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/vendor/thor/lib/thor.rb:527:in `dispatch'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/cli.rb:34:in `dispatch'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/vendor/thor/lib/thor/base.rb:584:in `start'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/cli.rb:28:in `start'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/exe/bundle:28:in `block in <top (required)>'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/lib/bundler/friendly_errors.rb:117:in `with_friendly_errors'
	from /Users/tkomiya/.dotfiles/_rbenv/versions/3.3.2/lib/ruby/gems/3.3.0/gems/bundler-2.5.3/exe/bundle:20:in `<top (required)>'
	from /Users/tkomiya/.rbenv/versions/3.3.2/bin/bundle:25:in `load'
	from /Users/tkomiya/.rbenv/versions/3.3.2/bin/bundle:25:in `<main>'
```

## Additional information

The RBS file `sig/example.rbs` was generated from `lib/example.rb` via `rbs prototype rb` command.
You can regenerate it through the following command:

    bundle exec rbs prototype rb --out-dir sig/ lib


Additionally, I got this error since I was updated to rbs-3.5.1 from 3.5.0.
