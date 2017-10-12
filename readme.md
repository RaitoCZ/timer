# Simple timer

[![Build Status](https://img.shields.io/travis/raitocz/timer.svg)](https://travis-ci.org/raitocz/timer)
[![Test Coverage](https://img.shields.io/coveralls/raitocz/timer.svg)](https://coveralls.io/github/raitocz/timer)
[![Dependencies](https://img.shields.io/versioneye/d/php/raitocz:timer.svg)](https://versioneye.com/php/raitocz:timer)
[![Version](https://img.shields.io/packagist/v/raitocz/timer.svg)](https://packagist.org/packages/raitocz/timer)
[![Licence](https://img.shields.io/packagist/l/raitocz/timer.svg)](https://packagist.org/packages/raitocz/timer)

## Table of contents

- [Installation](#installation)
- [Introduction](#introduction)
- [Basic usage](#basic-usage)
- [Checkpoints](#checkpoints)
- [Duration between checkpoints](#duration-between-checkpoints)

## Installation

`composer require raitocz/timer`

## Introduction

This very simple library can be used to benchmark execution times of your code, or simply whenever you need a stopwatch.

## Basic usage

You can retrieve duration between the timer start and stop.

```php
$timer = new Timer();
$timer->start();
sleep(1);
$timer->stop();
echo $timer->getDuration(); // 1.0234
```

## Checkpoints

You can create custom checkpoints whenever and retrieve the elapsed time until the checkpoint was reached.

```php
$timer = new Timer();
$timer->start();
$timer->createCheckpoint('foo');
$timer->stop();

$timer->getStartTime(); // returns start time in microseconds
$timer->getStopTime(); // returns stop time

$timer->getCheckpoint('start'); // returns start time
$timer->getCheckpoint('stop'); // returns stop time
$timer->getCheckpoint('foo'); // returns time of the checkpoint foo
```

## Duration between checkpoints

You can measure duration between the checkpoints.

```php
$timer = new Timer();
$timer->createCheckpoint('foo');
sleep(1);
$timer->createCheckpoint('bar');

// returns time elapsed since checkpoint foo till now
$timer->getDuration('foo');
// returns duration between checkpoints foo and bar
$timer->getDuration('foo', 'bar');

$timer->stop();
// returns time between checkpoints foo and stop
$timer->getDuration('foo');
```
