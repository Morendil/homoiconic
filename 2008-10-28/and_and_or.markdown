and and or
===

In a comment on [Ruby Stylista](http://www.pathf.com/blogs/2008/10/ruby-stylista/), I mentioned how I use the `and` and `or` keywords in Ruby. To refresh, `and` and `or` work just like `&&` and `||`, only with very low precedence. For example:

	foo = 5 && 10; foo
	  => 10
	foo = (5 && 10); foo;
	  => 10
	foo = 5 and 10; foo
	  => 5
	(foo = 5) and 10; foo
	  => 5

You can see from the examples how the expression is 'grouped' by the very low precedence of `and` and `or`. Since they have such low precedence, I use them to create conditional execution, to tie two imperative statements together. For example, you could write:

	foo = fubar() if do_something()

This reverses the order of execution, putting the clause `do_something()` after `foo = fubar()` even though it will happen in the opposite order. If you wish to write them in temporal order, you can use `and`:

	do_something() and foo = fubar()

This puts "first things first." Likewise you can use `or` to reverse the order of an `unless` statement. Instead of:

	raise 'fubar' unless do_something()

You could write:

	do_something() or raise 'fubar'

Again putting the first thing first. I normally only do this if both clauses are imperative. In other words, I would not rewrite either of these statements because the predicate is a query with no side-effects:

	foo = fubar() if something.blank?
	raise 'fubar' unless something?

The predicate seems less important than the consequent, which suggests that it should come second even though the test is performed first.

---

Recent work:

* [Kestrels, Quirky Birds, and Hopeless Egocentricity](http://leanpub.com/combinators), all of my writing about combinators, collected into one e-book.
* [What I've Learned From Failure](http://leanpub.com/shippingsoftware), my very best essays about getting software from ideas to shipping products, collected into one e-book.
* [Katy](http://github.com/raganwald/Katy), a library for writing fluent CoffeeScript and JavaScript using combinators.
* [YouAreDaChef](http://github.com/raganwald/YouAreDaChef), a library for writing method combinations for CoffeeScript and JavaScript projects.

---

[Reg Braithwaite](http://reginald.braythwayt.com) | [@raganwald](http://twitter.com/raganwald)