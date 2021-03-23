<template>
    <div id="contact" class="p-4">
        <div class="row justify-content-center mt-3 mb-3">
            <div class="col-lg-4">
                <h2>Have Any Questions?</h2>
                <p>Contact us by filling out the information below</p>

                <form>
                    <div class="form-group text-left">
                        <input type="email"
                            class="form-control"
                            placeholder="Enter Your Email"
                        >
                        <textarea class="form-control mt-3"
                            placeholder="Enter Your Message" 
                            rows="5">
                        </textarea>
                    </div>
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data () {
        return {
            count: 0
        }
  }
}
</script>

<style scoped>
    #contact {
        background-color: #57AEAF;
        text-align: center;
        color: #2c3e50;
    }
</style>