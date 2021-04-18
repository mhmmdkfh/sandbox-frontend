<template>
    <div>
        <PartialsTitle title="Sandbox Frontend" />

        <div class="p-3 card">
            <div class="overflow-y" style="height: 70vh;">
                <div class="row">
                    <div class="col-md-4">
                        <div class="input">
                            <div class="row">
                                <div class="col-sm-10 col-md-9 ">
                                    <FormInput name="Input Book" :val="InputBook" @value="(val)=>InputBook=val" />
                                </div>
                                <div class="col-sm-2 col-md-3">
                                    <button type="button" class="btn btn-outline-info rounded-pill btn-Book" @click="addbook"><i class="fas fa-plus"></i></button>
                                </div>
                            </div>
                        </div>
                        <ul type="none" class="p-1">
                            <li class="d-flex justify-content-between align-items-center mb-3" v-for="(book,i)  in BookList" :key="i">{{book}}
                                <button class="btn btn-outline-danger rounded-pill" @click="deleteBook(i)"><i class="fas fa-minus"></i></button>
                            </li>
                            <li></li> 
                        </ul>
                    </div>
                    <div class="col-md-4">
                        <div class="input">
                            <div class="row">
                                <div class="col-sm-10 col-md-9">
                                    <FormInput name="Input Reader" :val="InputReader" @value="(val)=>InputReader=val" />
                                </div>
                                <div class="col-sm-2 col-md-3">
                                    <button type="button" class="btn btn-outline-info rounded-pill btn-Book" @click="addreader"><i class="fas fa-plus"></i></button>
                                </div>
                            </div>
                        </div>
                        <ul type="none" class="p-1">
                            <li class="d-flex justify-content-between align-items-center mb-3" v-for="(read,i)  in ReaderList" :key="i ">{{read}}
                                <button class="btn btn-outline-danger rounded-pill" @click="deleteReader(i)"><i class="fas fa-minus"></i></button></li> 
                        </ul>
                    </div>
                    <div class="col-md-4">
                        <div>
                            <div class="row mb-3">
                                <div class="col-sm-10 col-md-9">
                                    <section>
                                        <label for="Reader">Choose Reader</label>
                                        <select name="reader" id="Reader" class="form-control" v-model="InputReaderBook1">
                                            <option selected disabled value="">Choose Reader</option>
                                            <option v-for="(reader,i) in ReaderList" :key="i" :val="InputReaderBook1" @value="(val)=>InputReaderBook1=val"> {{reader}}</option>
                                        </select>
                                    </section>
                                    <section>
                                        <label for="Book">Choose Book</label>
                                        <select name="book" id="Book" class="form-control" v-model="InputReaderBook2">
                                            <option selected disabled value="">Choose Book</option>
                                            <option v-for="(book,i) in BookList" :key="i" :val="InputReaderBook2" @value="(val)=>InputReaderBook2=val"> {{book}}</option>
                                        </select>
                                    </section>
                                </div>
                                <div class=" col-sm-2 col-md-3">
                                    <button type="button" class="btn btn-outline-info rounded-pill btn-BookReader ml-3" @click="addreaderbook"><i class="fas fa-plus"></i></button>
                                </div>
                            </div>
                        </div>
                        <ul type="none" class="p-1">
                            <li class="d-flex justify-content-between align-items-center mb-3" v-for="(RH,i)  in ReaderHistoryList " :key="i ">{{RH}}
                                <button class="btn btn-outline-danger rounded-pill" @click="deleteRH(i)"><i class="fas fa-minus"></i></button></li> 
                        </ul>
                    </div>
                </div>
            </div>
            
        </div>
        
    </div>
</template>
<script>
export default {
    data() {
        return {
            InputBook: "",
            Book:"",
            Reader: "",
            InputReader: "",
            InputReaderBook1: "",
            InputReaderBook2: "",
            BookList: ["The Last Wizard", "Of The Century"],
            ReaderList: ["Muhammad Kifahi", "Ghany Abdillah Ersa"],
            ReaderHistoryList: ["Muhammad Kifahi - Of The Century"],
        };
    },
    methods: {
        addbook() {
            if(this.InputBook == ""){
                swal({text: "The name of the book cannot be empty", icon: "error"});
            }else{
                    swal({
                        title: "Are you sure?",
                        text: "Do you want to add data",
                        icon: "warning",
                        buttons: true,
                        dangerMode: true
                    }).then((willAdd) => {
                        if(willAdd){
                            this.BookList = [...this.BookList, this.InputBook];
                            swal({text: "Data added successfully", icon: "success"});
                        } else {

                        };
                    });
            };
        },
        addreader() {
            if(this.InputReader == ""){
                swal({text: "The name of the reader cannot be empty", icon: "error"});
            }else{
                    swal({
                        title: "Are you sure?",
                        text: "Do you want to add data",
                        icon: "warning",
                        buttons: true,
                        dangerMode: true
                    }).then((willAdd) => {
                        if(willAdd){
                            this.ReaderList = [...this.ReaderList, this.InputReader];
                            swal({text: "Data added successfully", icon: "success"});
                        } else {

                        };
                    });
            };
        },
        addreaderbook() {
            if(this.InputReaderBook1 == ""){
                swal({text: "Data cannot be empty", icon: "error"});
            }else{
                if(this.InputReaderBook2 == ""){
                    swal({text: "Data cannot be empty", icon: "error"});
                }else{
                    swal({
                        title: "Are you sure?",
                        text: "Do you want to add data",
                        icon: "warning",
                        buttons: true,
                        dangerMode: true
                    }).then((willAdd) => {
                        if(willAdd){
                            this.ReaderHistoryList = [...this.ReaderHistoryList, this.InputReaderBook1+ " - " +this.InputReaderBook2];
                            swal({text: "Data added successfully", icon: "success"});
                        } else {

                        };
                    });
                };
            };
            
        },
        deleteBook(i){
            swal({
                title: "Are you sure?",
                text: "Do you want to delete data",
                icon: "warning",
                buttons: true,
                dangerMode: true
            }).then((willDelete) => {
                if(willDelete){
                    this.BookList.splice(i,1);
                } else {

                };
            });
        },
        deleteReader(i){
            swal({
                title: "Are you sure?",
                text: "Do you want to delete data",
                icon: "warning",
                buttons: true,
                dangerMode: true
            }).then((willDelete) => {
                if(willDelete){
                    this.ReaderList.splice(i,1);
                } else {

                };
            });
        },
        deleteRH(i){
            swal({
                title: "Are you sure?",
                text: "Do you want to delete data",
                icon: "warning",
                buttons: true,
                dangerMode: true
            }).then((willDelete) => {
                if(willDelete){
                    this.ReaderHistoryList.splice(i,1);
                } else {

                };
            });
        },
    },
}
</script>