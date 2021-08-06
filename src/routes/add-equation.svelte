<script>
    import { onMount } from 'svelte';

    import jq from 'jquery';
    import initMathquill from '$lib/mathquill/mathquill.js';

    let problemSpan;
    let answerSpan;
    
    onMount(() => {
        const MathQuill = initMathquill(jq);
        const MQ = MathQuill.getInterface(2);

        MQ.StaticMath(jq(problemSpan)[0]);

        var answer = MQ.MathField(jq(answerSpan)[0], {
            handlers: {
                edit: function() {
                    //checkAnswer(answer.latex());
                }
            }
        });
    });
</script>

<p>
    Solve <span id="problem" bind:this={problemSpan}>ax^2 + bx + c = 0</span>:
    <span id="answer" bind:this={answerSpan}>x=</span>
</p>
