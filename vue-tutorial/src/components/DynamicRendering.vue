<script>
    export default {
      data() {
        return {
          message: 'Hello World!',
          counter: {
            count: 0
          }
        }
      }
    }
    </script>
    
    <template>
      <h1>{{ message }}</h1>
      <p>
       Reverse Hello World!
        {{ message.split('').reverse().join('') }}
      </p>
      <p>Count is: {{ counter.count }}</p>
    </template>