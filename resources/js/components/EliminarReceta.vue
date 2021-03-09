<template>
    <input type="submit" class="btn btn-danger d-block w-100 " value="Eliminar" v-on:click="eliminarReceta">
</template>
<script>
export default {
    props:['idReceta'],
           methods:{
            eliminarReceta(){
                this.$swal({
                    title:"Are yoy sure",
                    text: "Yout wont be able to revert this",
                    icon: 'warning',
                    showCancelButton: true,
                    confirmButtonColor:'#3085d6',
                    cancelButtonColor:'#d33',
                    confirmButtonText:'Si',
                    cancelButtonText:'NO'
                    }).then((result) =>{
                        if(result.isConfirmed){
                            const params={
                                id:this.idReceta
                            }
                            axios.post(`/recetas/${this.idReceta}`,{params,_method:'delete'})
                            .then(respuesta=>
                            {//console.log(respuesta);
                               this.$swal({
                               title:"Receta eliminada",
                               text: "Se ha eliminado la receta",
                               icon: 'success',
                               confirmButtonText:'aceptar',
                            })
                            this.$el.parentNode.parentNode.partenNode.removeChild(this,$el,parentNode.parentNode);
                            })
                            .catch(error=>{console.log(error);

                            })
                        }
            
                      })
            
            }
        }
}
</script>