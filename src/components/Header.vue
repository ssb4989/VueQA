<template>
    <div>
        <b-nav>
            <b-nav-item disabled><b>Random QA</b></b-nav-item>
            <b-nav-item disabled>Your Count : {{ numCorrect }}/{{ numTotal }}</b-nav-item>
        </b-nav>
    </div>    
</template>

<script>
export default {
    props:[
        'numCorrect',
        'numTotal'
    ]
}
</script>