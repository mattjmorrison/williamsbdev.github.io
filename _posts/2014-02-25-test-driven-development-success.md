---
layout: post
title: "Test Driven Development Success"
category: agile development
tags: [TDD]
---

Test Driven Development used to seem like such a stretch goal for me as a
programmer. Now it has become like breathing. I do not really think about it
but just do it. I do not write code that I intend to keep without a test. If I
am unsure how to solve the problem, I will spike code with the intent of
throwing the code away once I understand what I want the test to say.

I read Kent Beck's *Test-Driven Development* which was a good read after doing
TDD for nearly a year. I knew how to do test-drive code but hearing it
explained and some of the methods behind it made me appreciate the
process/journey more. I use the Python Django framework for web development so
my examples will be with Python. When starting, Kent Beck says to start with
your high level test that tests the end behavior. This test may be failing for
a little while until you can get it passing. So here is a scenario, you have an
endpoint for a worker where you can post the hours worked and the number of
widgets made and then the endpoint will take the widgets/hours to give the
output/hour. The complete code example can be found at
[tdd-example](https://github.com/williamsbdev/tdd-example). I tried to make
each commit a step I would take to help you walk through my thought process of
how I would test this application.

So given the example above, here is what the test would look like.

{% highlight python %}
class WorkerViewTests(TestCase):

    def test_worker_view_post_will_return_201(self):
        url = reverse('api:workers')
        data = {'name': 'Bob', 'hours': 10, 'widgets': 50}
        response = self.client.post(url, data=data)
        self.assertEqual(201, response.status_code)
{% endhighlight %}
