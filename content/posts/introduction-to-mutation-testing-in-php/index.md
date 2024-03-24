---
title: "An introduction into Mutation Testing in PHP"
date: 2024-03-23
description: "What on earth is mutation testing?"
draft: true
---
# What is mutation testing?
Well it's not this.
![Not these mutants](thumbnail.png)
## If mutation testing is the answer, what is the question?
 Well, the assurance of high-quality software relies not just on writing tests but on ensuring those tests are genuinely effective. So how do we measure this? *& that is the question.*
 
 **Mutation testing** is a technique designed to evaluate and improve the effectiveness of your test suite. By deliberately introducing small changes, or mutations, into the source code, mutation testing challenges your tests to catch these modifications, thereby enhancing the robustness of your testing tools.

It **wants** to create test failures, causing test failures means that you're tests are actually asserting what you expect. If the tests still pass despite your code changing, it's probably worth revisiting those tests. This is where just using code coverage as a metric lies to you.

# Why Mutation Testing Matters

Mutation testing transcends traditional testing by verifying that your tests do more than just pass, *shakes fist angrily at code coverage*, they must catch actual flaws.

![Yells at code coverage](yells-at-code-coverage.jpg "My meme skills need work.")

It ensures that tests are not superficially passing but are capable of detecting unintended behaviours, gaps in test coverage, and inadequacies in test assertions.

## Benefits

- **Detects Unintended Behaviour:** Uncovers scenarios not covered by existing tests.
- **Identifies Untested Code:** Highlights parts of the application lacking sufficient tests.
- **Improves Test Quality:** Exposes poorly written or ineffective tests.
- **Encourages Regular Test Maintenance:** Signals when tests need updates due to code changes.

## Detractors
The main detractor of mutation testing is time, if you think about how long your test suite takes to run now, then multiply that by however many mutants are spawned. Yeah it's a while, however there are work arounds such as only running git diff'd files or lines to help resolve this.

If you are running containerized integration tests, you will need to resolve the potential issue of state management between your database connections.


Full list of mutators can be found here: [Mutators in infection](https://infection.github.io/guide/mutators.html)
# Integrating Mutation Testing in PHP
## Infection
> Infection is a **PHP mutation testing library** based on AST (Abstract Syntax Tree) mutations. It works as a CLI tool and can be executed from your project’s root.
> 

https://infection.github.io/guide/index.html
## Types of Mutants in Mutation Testing
A few examples from the demo repository output found at the bottom of this post:

```
Warning: Escaped Mutant for Mutator "NullSafeMethodCall":

--- Original
+++ New
@@ @@
public function checkInventory(string $itemId) : int
{
$item = $this->repository->getItem($itemId);
-        $quantity = $item?->getQuantity();
+        $quantity = $item->getQuantity();
if ($quantity === null) {
// throw something
}


Warning: Escaped Mutant for Mutator "Identical":

--- Original
+++ New
@@ @@
{
$item = $this->repository->getItem($itemId);
$quantity = $item?->getQuantity();
-        if ($quantity === null) {
+        if ($quantity !== null) {
// throw something
}
if ($quantity == 0) {


Warning: Escaped Mutant for Mutator "GreaterThan":

--- Original
+++ New
@@ @@
if (empty($price)) {
$price = $this->getPrice($currency);
}
-        if ($discountPercentage > self::ZERO_PERCENT && $discountPercentage <= self::WHOLE_PERCENT) {
+        if ($discountPercentage >= self::ZERO_PERCENT && $discountPercentage <= self::WHOLE_PERCENT) {
$price *= 1 - $discountPercentage / 100;
$this->setPrice($price, $currency);
}


Warning: Escaped Mutant for Mutator "LogicalAnd":

--- Original
+++ New
@@ @@
if (empty($price)) {
$price = $this->getPrice($currency);
}
-        if ($discountPercentage > self::ZERO_PERCENT && $discountPercentage <= self::WHOLE_PERCENT) {
+        if ($discountPercentage > self::ZERO_PERCENT || $discountPercentage <= self::WHOLE_PERCENT) {
$price *= 1 - $discountPercentage / 100;
$this->setPrice($price, $currency);
}
}


Warning: Escaped Mutant for Mutator "IncrementInteger":

--- Original
+++ New
@@ @@
}
public function setPrice(float $price, string $currency) : void
{
-        $this->prices[$currency] = round($price, 2);
+        $this->prices[$currency] = round($price, 3);
}
}
```
## Installation via Composer

To integrate mutation testing into your PHP projects, you can use Infection, a mutation testing framework designed for PHP. Installing Infection is straightforward with Composer:

`composer require --dev infection/infection`

This command adds Infection to your project as a development dependency, enabling you to run mutation tests alongside your regular testing suite.

## Running Mutation Tests

Once installed, you can execute mutation tests to evaluate the quality of your test suite. Here's a basic command to start mutation testing with Infection:

`vendor/bin/infection --min-msi=70 --min-covered-msi=75`

This command runs mutation tests on your project, with the `min-msi` (minimum Mutation Score Indicator) and `min-covered-msi` (minimum Covered Code MSI) options set to ensure a certain threshold of test effectiveness.
# Usage
## Small Example Repo
https://github.com/matthewrobinsondev/mutation-testing-example-repo

There are 3 branches named `STEP-1`, `STEP-2` and `STEP-3`. The idea of these are to understand how the code coverage and MSI are different. Move on to the next step once you have worked on those tests to get them to 100% MSI.
## Pipeline
https://infection.github.io/guide/using-with-ci.html

# Conclusions
Mutation testing represents yet another powerful tool in the arsenal of PHP developers, aimed at enhancing the quality and effectiveness of test suites. By introducing these deliberate mutations into our source code, it challenges and strengthens our testing strategies, ensuring that our tests are not just passing but are genuinely robust.
# Resources
- https://www.techtarget.com/searchitoperations/definition/mutation-testing#:~:text=Mutation%20testing%2C%20also%20known%20as,cause%20errors%20in%20the%20program.
- https://medium.com/@maks_rafalko/infection-mutation-testing-framework-c9ccf02eefd1
- https://infection.github.io/guide/

