<template>
    <div class="container">
        <div class="row">

            <div class="col-md-6 shadow p-3 mb-5 bg-white rounded" id="boxShadow" >
                <form>
                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-12 col-md-offset-3">
                            <h1>From Handeling</h1>
                            <hr>
                            <div class="form-group">
                                <label for="email">Mail</label>
                                <input
                                        type="text"
                                        id="email"
                                        class="form-control"
                                        v-model="userData.email">
                            </div>
                            <div class="form-group">
                                <label for="password">Password</label>
                                <input
                                        type="password"
                                        id="password"
                                        class="form-control"
                                        v-model.lazy="userData.password">
                            </div>
                            <div class="form-group">
                                <label for="age">Age</label>
                                <input
                                        type="number"
                                        id="age"
                                        class="form-control"
                                        v-model="userData.age">
                            </div>

                        </div>
                    </div>
                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-12 col-md-offset-3 form-group">
                            <label for="message">Message</label><br>

                            <textarea
                                    id="message"
                                    rows="5"
                                    class="form-control"
                                    v-model="message">
                            </textarea>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                            <div class="form-group">
                                <label for="sendmail">
                                    <input
                                            type="checkbox"
                                            id="sendmail"
                                            value="SendMail"
                                            v-model="sendMail"> Send Mail
                                </label>&nbsp;
                                <label for="sendInfomail">
                                    <input
                                            type="checkbox"
                                            id="sendInfomail"
                                            value="SendInfoMail"
                                            v-model="sendMail"> Send Infomail
                                </label>
                            </div>

                        </div>
                    </div>
                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                            <label for="male">
                                <input
                                        type="radio"
                                        id="male"
                                        value="Male"
                                        v-model="gender"> Male
                            </label>
                            <label for="female">
                                <input
                                        type="radio"
                                        id="female"
                                        value="Female"
                                        v-model="gender"> Female
                            </label>
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
                            <label for="priority">Priority</label>
                            <select
                                    id="priority"
                                    class="form-control"
                                    v-model="selectedPriority">
                                <option v-for="priority in priorities" :key="priority">
                                    {{priority}}
                                </option>
                            </select>
                        </div>
                    </div>

                    <hr>
                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                            <button
                                    class="btn btn-primary"
                                    @click.prevent="submitted">Submit!
                            </button>
                        </div>
                    </div>
                </form>         
            </div>

            <div class="col-md-6" v-if="is_submitted">
                <div class="row" id="content">
                    <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-12 col-md-offset-3">
                        <div class="panel panel-default">
                            <div class="panel-heading">
                                <h4>Your Data</h4>
                            </div>
                            <div class="panel-body">
                                <p>Mail: {{ userData.email }}</p>
                                <p>Password: {{userData.password}}</p>
                                <p>Age: {{ userData.age }}</p>
                                <p style="white-space: pre-line;">Message: {{ message }}</p>
                                <p><strong>Send Mail?</strong></p>
                                <ul>
                                    <li v-for="mail in sendMail" :key="mail">
                                        {{mail}}
                                    </li>
                                </ul>
                                <p>Gender: {{gender}}</p>
                                <p>Priority: {{ selectedPriority }}</p>
                                <p>Switched:</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
          
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                userData : {
                    email : '',
                    password : '',
                    age : 0
                },
                message : '',
                sendMail : [],
                gender : '',
                selectedPriority : 'Medium',
                priorities : ['High', 'Medium', 'Low'],
                is_submitted : false
            }
        },

        methods : {
            submitted(){
                this.is_submitted = true;
            }
        }
    }
</script>

<style>

    ul li{
        list-style-type : none;

    }

    #boxShadow{
        margin:30px 0px;
    }
    #content{
        padding-left:30px;
        margin-top:30px;
    }
 
</style>