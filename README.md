# README – Módulo de Reviews (Laravel API + Sanctum) ## 1. Autenticación Los endpoints
protegidos requieren: Authorization: Bearer Accept: application/json Content-Type: application/json ##
2. Endpoints de Autenticación POST /api/register { "name": "Alex", "email": "alex@example.com",
"password": "12345678", "password_confirmation": "12345678" } POST /api/login { "email":
"alex@example.com", "password": "12345678" } POST /api/logout ## 3. Endpoints de Reviews POST
/api/products/{productId}/reviews { "rating": 5, "comment": "Muy buen producto" } GET
/api/products/{productId}/reviews PUT /api/reviews/{id} { "rating": 4, "comment": "Mejor de lo esperado"
} DELETE /api/reviews/{id} GET /api/products/{productId}/reviews/average ## 4. Rutas usadas
(api.php) Route::post('/register', [...]); Route::post('/login', [...]);
Route::middleware('auth:sanctum')->group(function () { Route::post('/products/{productId}/reviews',
[...]); Route::get('/products/{productId}/reviews', [...]);
Route::get('/products/{productId}/reviews/average', [...]); Route::put('/reviews/{id}', [...]);
Route::delete('/reviews/{id}', [...]); Route::post('/logout', [...]); }); ## 5. Modelo Review protected $fillable
= [ 'rating','comment','user_id','product_id' ]; ## 6. Instrucciones para frontend 1. Obtener token. 2.
Enviar Bearer en todas las requests. 3. CRUD requiere autenticación. ## 7. Commit git checkout
feature/reviews git add . git commit -m "Módulo de reviews completado" git push origin feature/reviews
