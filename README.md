# switch-button
Vuejs stand alone plugin 

# How it works 
it is simple and you can modify it as per your need.
it accepts only true or false as model you can used it in loop like selecting and deselecting products
you can change parent components values or objects value on change of value of this components

#props 

# Props that can be passed to this Component

<table>
     <tr> 
        <th>Props </th>
        <th>Default </th>
        <th>Description </th>
     </tr>   
</table>   


# Example
```
<script>
   import SwitchButton from "../form/Switch";
  export default{
  components: {
      SwitchButton,
      },
       methods:{
            submitForm($type){
               
            },
            onProductSubsrcibe(value){
                console.log(value);
            },
            onChange(value){
                console.log(value);
            }
        },
  }
 </script> 
<template>
   <div>
     <table>
      <tr v-for="(product,key) in initialData.subscription">
          <td>
              <div class="col-md-10">
                  <p>{{ product.name }} </p>
                   <div class="col-md-2 text-right">
                   <switch-button :name="getName(key)" @change="onProductSubsrcibe" :checked="product.value" v-model="product.value" />
              </div>
          </td>
      </tr>
    </table>
    <table>
       <tbody>
                <tr >
                    <td width="90%"><h4>Pauzeer je abonnement</h4></td>
                    <td >
                        <switch-button
                                :name="'is_agree'"
                                :checked="true"
                                v-model="is_agree"
                                @change="onChange"
                        />

                    </td>
                </tr>
    </table>
    </div>
</template>                
 ```               
